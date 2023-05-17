## 0x1A. Application server

DevOps	SysAdmin

 By: Sylvain Kalache, co-founder at Holberton School

### Concepts

* For this project, we expect you to look at these concepts:

	+ [Web Server](https://intranet.alxswe.com/concepts/17)
	+ [Server](https://intranet.alxswe.com/concepts/67)
	+ [Web stack debugging](https://intranet.alxswe.com/concepts/68)

## Resources:books:
Read or watch:
* [Application server vs web server](https://intranet.hbtn.io/rltoken/RerpYBxsgrpIorHjbDgulw)
* [How to Serve a Flask Application with Gunicorn and Nginx on Ubuntu 16.04](https://intranet.hbtn.io/rltoken/uosy5QXdMbDPA1tFTR1eoA)
* [Running Gunicorn](https://intranet.hbtn.io/rltoken/QTnnkj6vfQV9ovW_eYWWDQ)
* [Be careful with the way Flask manages slash](https://intranet.hbtn.io/rltoken/whE8do28ZiJJoJLyb1ACwA)
* [route](https://intranet.hbtn.io/rltoken/JLjrXD4MLS3rUkQr5QyxtA)
* [Upstart documentation](https://intranet.hbtn.io/rltoken/oQPs-o5UUcZkxOw5sNIM0g)



![](https://cdn.educba.com/academy/wp-content/uploads/2019/04/What-is-Application-Server-1.jpg.webp)

![](https://cdn.educba.com/academy/wp-content/uploads/2019/04/What-is-Application-Server-1.1.png)


Your web infrastructure is already serving web pages via Nginx that you installed in [your first web stack project](https://github.com/sammykingx/alx-system_engineering-devops/tree/master/0x0C-web_server). While a web server can also serve dynamic content, this task is usually given to an application server. In this project you will add this piece to your infrastructure, plug it to your __Nginx__ and make is serve your __Airbnb clone project.__

## Project Requirements

- A README.md file, at the root of the folder of the project, is mandatory
- Everything Python-related must be done using `python3`
- All config files must have comments
- All your files will be interpreted on `Ubuntu 16.04 LTS`
- All your files should end with a new line
- All your Bash script files must be executable
- Your Bash script must pass `Shellcheck` (`version 0.3.7-5~ubuntu16.04.1` via `apt-get`) without any error
- The first line of all your Bash scripts should be exactly `#!/usr/bin/env bash`
- The second line of all your Bash scripts should be a comment explaining what is the script doing.

### Project task
- 0. Set up development with Python
	Let’s serve what you built for AirBnB clone v2 - Web framework on web-01. This task is an exercise in setting up your development environment, which is used for testing and debugging your code before deploying it to production.

	__Requirements:__

	- Make sure that task #3 of your SSH project is completed for web-01. The checker will connect to your servers.
	- Git clone your AirBnB_clone_v2 on your web-01 server.
	- Configure the file web_flask/0-hello_route.py to serve its content from the route /airbnb-onepage/ on port 5000.
	- Your Flask application object must be named app (This will allow us to run and check your code).

#### Solving task 0
- git clone Airbnb_clone_v2
- edit the file 0-hello_route.py by replacing "/" with "airbnb_onepage"

```bash
(venv) ubuntu@64820-web-01:~/AirBnB_clone_v2$ python3 -m web_flask.0-hello_route
 * Serving Flask app '0-hello_route'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://10.247.26.30:5000
Press CTRL+C to quit
127.0.0.1 - - [10/Feb/2023 21:00:05] "GET /airbnb-onepage HTTP/1.1" 200 -

```
__After Fixing__

```bash
ubuntu@64820-web-01:~$ curl localhost:5000/airbnb_onepage
Hello HBNB!ubuntu@64820-web-01:~$
```


## Learning Objectives:bulb:
What you should learn from this project:

---


### [0. Set up development with Python](./README.md)

### [1. Set up production with Gunicorn](./2-app_server-nginx_config)
* Now that you have your development environment set up, let’s get your production application server set up with Gunicorn on web-01, port 5000. You’ll need to install Gunicorn and any libraries required by your application. Your Flask application object will serve as a WSGI entry point into your application. This will be your production environment. As you can see we want the production and development of your application to use the same port, so the conditions for serving your dynamic content are the same in both environments.


### [2. Serve a page with Nginx](./3-app_server-nginx_config)
* Building on your work in the previous tasks, configure Nginx to serve your page from the route /airbnb-onepage/


### [3. Add a route with query parameters](./4-app_server-nginx_config)
* Building on what you did in the previous tasks, let’s expand our web application by adding another service for Gunicorn to handle. In AirBnB_clone_v2/web_flask/6-number_odd_or_even, the route /number_odd_or_even/<int:n> should already be defined to render a page telling you whether an integer is odd or even. You’ll need to configure Nginx to proxy HTTP requests to the route /airbnb-dynamic/number_odd_or_even/(any integer) to a Gunicorn instance listening on port 5001. The key to this exercise is getting Nginx configured to proxy requests to processes listening on two different ports. You are not expected to keep your application server processes running. If you want to know how to run multiple instances of Gunicorn without having multiple terminals open, see tips below.


### [4. Let's do this for your API](./5-app_server-nginx_config)
* Let’s serve what you built for AirBnB clone v3 - RESTful API on web-01.


### [5. Serve your AirBnB clone](./gunicorn.service)
* Let’s serve what you built for AirBnB clone - Web dynamic on web-01.


### [6. Deploy it!](./4-reload_gunicorn_no_downtime)
* Once you’ve got your application server configured, you want to set it up to run by default when Linux is booted. This way when your server inevitably requires downtime (you have to shut it down or restart it for one reason or another), your Gunicorn process(es) will start up as part of the system initialization process, freeing you from having to manually restart them. For this we will use systemd. You can read more about systemd in the documentation posted at the top of this project but to put it succinctly, it is a system initialization daemon for the Linux OS (amongst other things). For this task you will write a systemd script which will start your application server for you. As mentioned in the video at the top of the project, you do not need to create a Unix socket to bind the process to.


---
