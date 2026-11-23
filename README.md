



https://devdocs.prestashop-project.org/8/basics/installation/system-requirements/




:80 {
    redir https://localhost
}

:443 {
    reverse_proxy prestashop:8080
    tls luca.sain@outlook.com  # Reemplaza con tu email para obtener certificados SSL
}
localhost {
	respond "Hello, world!"
}

localhost:2016 {
	respond "Goodbye, world!"
}


:80 {
	respond "Im the port 80, Hello!"
}

:443 {
	respond "Goodbye, world!"
    tls luca.sain@outlook.com  # Reemplaza con tu email para obtener certificados SSL
}
:2016 {
	respond "Im the port 2016, Hello!"
}











localhost {
    redir https://localhost
}

localhost:443 {
    respond "Im the port 443, Hello!"
}
localhost:2016 {	
    respond "Im the port 2016, Hello!"
}







    handle {
        reverse_proxy http://prestashop:8080 {
        header_up X-Forwarded-Host {host}
            # Frontend must render the page under 20 seconds
            transport http {
                response_header_timeout 20s
            }
        }
    }