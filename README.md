# run-serenity-scripts
Docker image for running Serenity BDD tests in container.

Image contains the following dependencies intalled:

* OpenJDK
* Maven
* XVFB
* Firefox
* Chrome & ChromeDriver

To run Serenity BDD tests in container switch to the folder with your tests in run the following command:

    docker run --rm -i -v "$PWD":/home/remoteuser/serenity-project/ alexhalkin/run-serenity-scripts /bin/bash -c "Xvfb :99 & export DISPLAY=:99 && mvn clean verify -Dwebdriver.driver=firefox -Dserenity.outputDirectory=/home/remoteuser/serenity-project/report/firefox"

You may skip serenity.outputDirectory parameter if you want to save generate reports to the default output folder (target/serenity/site/)

In order to run tests using Chrome browser just use "chrome" as a value for webdriver.driver parameter. Example:

    docker run --rm -i -v "$PWD":/home/remoteuser/serenity-project/ alexhalkin/run-serenity-scripts /bin/bash -c "Xvfb :99 & export DISPLAY=:99 && mvn clean verify -Dwebdriver.driver=chrome -Dserenity.outputDirectory=/home/remoteuser/serenity-project/report/custom"
