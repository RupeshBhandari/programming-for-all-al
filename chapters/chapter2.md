# Chapter 2: Setting Up Your AL Development Environment

## System Requirements
To develop with AL, you need a compatible operating system, sufficient hardware resources, and the necessary software tools. Typically, you'll need:

- Windows 10 or later
- Visual Studio Code
- AL Language extension for Visual Studio Code
- Access to a Business Central sandbox environment

## Installing AL Tools and Extensions
Install Visual Studio Code: Download and install Visual Studio Code from the official website.
Add the AL Language Extension: In Visual Studio Code, navigate to the Extensions view and search for "AL Language". Install the extension.
Set Up a Sandbox Environment: Access the Microsoft Dynamics 365 Business Central Admin Center to create a sandbox environment for testing and development.

## Configuring Your Development Environment in Visual Studio Code
After installing the necessary tools, configure your development environment:

- Create a New AL Project: Use the Command Palette in Visual Studio Code to run the AL: Go! command, creating a new AL project with the necessary files and folders.
- Set Up Launch Configurations: Configure the launch.json file to connect to your Business Central sandbox environment.
- Install Dependencies: Use the dependencies section in app.json to include any required libraries or extensions.