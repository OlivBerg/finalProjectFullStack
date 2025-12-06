# Final Full Stack Project

## Brief

This application is meant to resemble a BestBuy webapp using a microservices architecture deployed on Azure AKS. We forked each application from the repos shared and modified them to be BestBuy-like.

I used AI to help me style and restructure the pages of the we store-front repo and manually modified the product-service to display product BestBuy would typecally sale. I have also modified the objet we create in product-service to incorporate rating, discounts and amout of reviews so that the website looks and feel more authentic.

### Updated Architecture

![Updated Architecture](/finalFullStack.drawio.png)

### Store-Front

This is a Vue.js app that simulates a store front. It is meant to be used in conjunction with the product-service and order-service. The app is extremely simple in that it only has a cart and a order submission button. When the order submission button is clicked, the cart is emptied and the order is sent to the order service. Currently there is no order checkout pages to collect any customer information.

### Store-Admin

This is a Vue.js app that simulates a store admin portal where users can manually process orders, and manage products. It is meant to be used in conjunction with the product-service and makeline-service.

### Order-Service

This is a Fastify app that provides an API for submitting orders. It is meant to be used in conjunction with the store-front app.

It is a simple REST API that allows you to add an order to a message queue that supports the AMQP 1.0 protocol.

### Product-Service

This is a Rust app that simulates a product catalog. It is meant to be used in conjunction with the store-front and store-admin apps.

This app is a simple REST API that allows you to get a list of products, get a single product, update a product, and add a product.

Products are loaded into memory and not persisted. So if the app is restarted, the products will be reloaded.

### Makeline-Service

This is a Golang app that provides an API for processing orders. It is meant to be used in conjunction with the store-admin app.

It is a simple REST API written with the Gin framework that allows you to process orders from a RabbitMQ queue and send them to a MongoDB database.

## Deployment

1. Create an AKS service on Azure
2. On a terminal
3. Login to your azure account using the following command:

```
az login
```

4. Set the cluster subscription using the command shown in the portal :

```
az account set --subscription 'subscribtion-id'
```

5. Copy the command shown in the portal for configuring kubectl (it will look something like this):

```
az aks get-credentials --resource-group <resource group name> --name <cluster name>
```

6. Apply the two yml file yaml file in the deployment folder

```
kubectl apply -f final_project.yaml
kubectl apply -f config-maps.yaml
```

7. Check if the deployment is working:

```
kubectl get pods
```

or/and

```
kubectl get services
```

## Links

[Youtube](https://youtu.be/s352zD9rtIM)
[Store-Front](https://github.com/OlivBerg/store-front-L8)
[Store-Admin](https://github.com/OlivBerg/store-admin-L8)
[Order-Service](https://github.com/OlivBerg/order-service-L8)
[Product-Service](https://github.com/OlivBerg/product-service-L8)
[Makeline-Service](https://github.com/OlivBerg/makeline-service-L8)
