# EX01 Developing a Simple Webserver

# Date:07/10/2024
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
```
from importlib.resources import contents
from django.shortcuts import render
from django.http import HttpResponse

contents='''<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lenovo ThinkPad E16 Gen 1</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #e0f7ff;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .specs-table {
            width: 50%;
            background-color: #2a2a84;
            color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        .specs-table h1 {
            text-align: center;
        }
        .specs-table table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        .specs-table th, .specs-table td {
            padding: 10px;
            text-align: left;
        }
        .specs-table tr:nth-child(even) {
            background-color: rgba(255, 255, 255, 0.1);
        }
    </style>
</head>
<body>
    <div class="specs-table">
        <h1>Lenovo ThinkPad E16 Gen 1</h1>
        <table>
            <tr>
                <td><strong>Processor:</strong></td>
                <td>13th Gen Intel® Core™ i5-1335U</td>
            </tr>
            <tr>
                <td><strong>Memory:</strong></td>
                <td>16GB LPDDR5 RAM</td>
            </tr>
            <tr>
                <td><strong>Display:</strong></td>
                <td>16-inch Full HD (1920 x 1200), 16:10 aspect ratio</td>
            </tr>
            <tr>
                <td><strong>Graphics:</strong></td>
                <td>NVIDIA GeForce GTX 1650</td>
            </tr>
            <tr>
                <td><strong>Storage:</strong></td>
                <td>Up to 1TB PCIe NVMe SSD</td>
            </tr>
            <tr>
                <td><strong>Build:</strong></td>
                <td>Lightweight aluminum chassis, ~1.8kg</td>
            </tr>
            <tr>
                <td><strong>Battery:</strong></td>
                <td>57Wh with rapid charging</td>
            </tr>
            <tr>
                <td><strong>Ports:</strong></td>
                <td>USB-C, HDMI, and other options</td>
            </tr>
            <tr>
                <td><strong>Operating System:</strong></td>
                <td>Windows 11</td>
            </tr>
        </table>
    </div>
</body>
</html>
'''

def app(request):
    return HttpResponse("Hello India")
from http.server import HTTPServer,BaseHTTPRequestHandler
class MyServer(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(contents.encode())
print("This is my webserver")
server_address =('',8000)
httpd = HTTPServer(server_address,MyServer)
httpd.serve_forever()
'''
urls.py

from tempfile import template
from django.contrib import admin
from django.urls import path
from app.views import MyServer


urlpatterns = [
    path('admin/', admin.site.urls),
    # path('new/',views.trial),
    # path('page/',views.slot),
    # path('home/',template.slot),
    path('server/',MyServer.as_view())
]
```
# OUTPUT:

![Screenshot 2024-12-05 184439](https://github.com/user-attachments/assets/ad0601b7-b82f-4ccc-bed7-bb5163408f19)

![Screenshot 2024-12-07 112247](https://github.com/user-attachments/assets/6a5ab00b-ddb2-426b-8b11-2df8c6060598)


# RESULT:
The program for implementing simple webserver is executed successfully.
