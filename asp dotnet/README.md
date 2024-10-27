Some how the dockerfile didn't work with google cloud platform so i recommend using the file google-docker to work with it

<h3> Self-hosting journey with cloudflare tunnel </h3>

<br>First, I built a Docker image and ran it locally.</br>

<br>
    - Everything worked perfectly, so I decided to use tunnel to expose my port to the internet for my final thesis.
    
    - I chose HTTPS instead of HTTP because I didn't notice that my Docker container only supports HTTP.
    
    - After researching, I switched to HTTP + IPv4 address, but it returned a blank page. However, when I tested it with Postman and curl /swagger/v1/swagger.json, everything was fine except that the SwaggerUI didn't appear as expected. I searched for answers and found discussions about the same problem, but most of them had already been resolved by updating to the latest version. However, I was already on the latest version.
    
    - After hours of research, I sent the API URL to my friend and asked them to run it on a different browser. Surprisingly, it worked normally.
    
    In conclusion, when running with a Docker container and tunneling it through Cloudflare, SwaggerUI may not work with Chrome and IE, but it works perfectly fine with OperaX. I didn't have time to test it on other browsers, but I believe that if we disable certain policies that prevent Cloudflare, it will work.
</br>
