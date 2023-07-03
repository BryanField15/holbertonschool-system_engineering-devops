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