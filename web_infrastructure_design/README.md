# 0-Simple Web Stack

This is a basic guide and explanation of a simple web infrastructure. It will help you understand the role of different components in a server environment and the related issues you might face. This setup comprises of a single server, hosting a website reachable via www.foobar.com.

## Specifics to explain about this infrastructure

- **Server**: A server is a computer that provides data to other computers (clients). It manages network resources and can run one or more services as required.
- **Domain name**: The domain name is the human-friendly version of the website's IP address. It is registered through a domain registrar, and mapped to the server's IP address using DNS.
- **DNS record**: The 'www' in 'www.foobar.com' is a type of DNS record. It's a subdomain of 'foobar.com', typically used to designate the web service.
- **Web server**: The web server is responsible for handling HTTP requests from users' browsers, serving up the appropriate web pages or resources, and dealing with static content.
- **Application server**: The application server handles any dynamic website content. It processes the business logic of the website, interacting with the database as needed.
- **Database**: The database stores, retrieves and manages data for the web application.
- **Communication**: The server communicates with the user's computer using the Hypertext Transfer Protocol (HTTP) or its secure version, HTTPS.

## Potential issues with this infrastructure

- **Single Point of Failure (SPOF)**: As all services (web server, application server, database) are hosted on a single server, if that server goes down, the entire website becomes unavailable.
- **Maintenance downtime**: Whenever maintenance is required (like deploying new code), the web server needs to be restarted. This results in downtime, making your website unavailable during that period.
- **Scalability**: In case of a sudden surge in traffic, this infrastructure cannot scale up to handle the load, leading to potential performance issues or server crashes.

# 1-Distributed Web Infrastructure

This outlines the design of a distributed web infrastructure. It details a three-server setup that hosts the website www.foobar.com.
## Specifics to explain about this infrastructure

- **Additional elements**: With a distributed setup, the additional servers and load balancer are introduced to increase the reliability and resilience of the system. The load balancer is particularly important as it ensures that traffic is evenly distributed across all available servers, avoiding overloading a single server and potentially causing it to crash.
- **Distribution algorithm**: Load balancers can use a variety of algorithms to determine how to distribute traffic. Common ones include Round Robin, Least Connections, and IP Hash. The selection of the distribution algorithm depends on the specific requirements and traffic patterns of your application.
- **Active-Active vs Active-Passive setup**: In an Active-Active setup, all servers are handling traffic. In an Active-Passive setup, one or more servers are kept on standby to take over if the active server fails. The choice between these setups depends on the specific requirements and budgetary constraints of your project.
- **Database Primary-Replica (Master-Slave) setup**: In this setup, the primary (or master) database processes write operations while one or more replica (or slave) databases synchronize with the primary database and handle read operations. This setup can help distribute database load and improve performance.
- **Primary node vs Replica node**: The primary node handles all write operations and updates the replica nodes. The replica nodes handle read operations, helping to distribute the load and reduce the strain on the primary node.

## Potential issues with this infrastructure

- **Single Point of Failure (SPOF)**: While a distributed setup can mitigate some risks, SPOF still exist. For instance, if your load balancer or the primary node of your database fails, it could cause significant issues.
- **Security**: Without a proper firewall and HTTPS, your setup is vulnerable to various types of attacks, such as DDoS attacks and data breaches.
- **Monitoring**: Without a proper monitoring solution, it might be difficult to identify and react to issues in a timely manner, which could lead to extended downtime or data loss.

# 2-Secured and Monitored Web Infrastructure

This covers the design of a secure, encrypted, and monitored web infrastructure. It details a three-server setup that hosts the website www.foobar.com.
## Specifics to explain about this infrastructure

- **Additional elements**: Each additional element enhances the security, encryption, and monitoring of your infrastructure. Firewalls protect your servers from malicious traffic, SSL certificate encrypts the data in transit, and monitoring clients help track the performance and health of your servers.
- **Firewalls**: Firewalls act as a security system for your servers, controlling the incoming and outgoing network traffic based on predetermined security rules.
- **HTTPS**: Serving traffic over HTTPS means that all communication between the browser and the website is encrypted, ensuring the confidentiality and integrity of the transferred data.
- **Monitoring**: Monitoring helps you to track the performance and health of your servers, alerting you to any potential issues before they can cause significant damage.
- **Data Collection**: Monitoring tools collect data about system performance, usage, and potential errors. This information is crucial for identifying and diagnosing problems, as well as optimizing performance.
- **Web Server QPS Monitoring**: QPS (Queries Per Second) is a measure of how much traffic your web server is handling. To monitor it, you could use a tool like the `mod_status` module in Apache or the `HttpStubStatusModule` module in Nginx.

## Potential issues with this infrastructure

- **SSL Termination at Load Balancer**: If SSL termination happens at the load balancer level, it means that traffic between the load balancer and the servers is not encrypted, which can be a security concern if your servers are not in a secure network.
- **Single MySQL Server for Writes**: Having only one MySQL server capable of accepting writes is a single point of failure. If that server goes down, write operations to the database will be halted until it is restored.
- **Uniform Server Components**: If all servers have the same components (database, web server, and application server), it might lead to inefficient resource use. It also does not take advantage of the possibilities of specializing servers to better handle specific tasks.

# 3-Scale-Up Web Infrastructure

Thistask focuses on the scale-up of a web infrastructure. It details the addition of another server and a load balancer configured as a cluster, as well as the separation of components (web server, application server, database) each to their own dedicated server. This setup hosts the website www.foobar.com.

## Specifics to explain about this infrastructure

- **Additional elements**: Each added element plays a crucial role in scaling up the infrastructure. The new server provides additional resources to handle more traffic. The clustered load balancer enhances the resilience and availability of your website, while splitting the components into dedicated servers allows for better performance and troubleshooting.
- **Server addition**: Adding a new server to the existing infrastructure helps to distribute the workload more effectively and handle higher traffic.
- **Load balancer cluster**: Configuring the new load balancer in a cluster with the existing one ensures high availability and better performance. If one load balancer fails, the other can seamlessly take over.
- **Split components**: By separating each component (web server, application server, and database) into their own dedicated servers, you can better optimize each for its specific task, handle more traffic, and reduce the risk of a single point of failure.