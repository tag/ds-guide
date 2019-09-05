# Using Docker


## Using the command line
As a reminder, use `cd` (**c**hange **d**irectory) to navigate, and `dir` (Windows) / `ls` (everything else) to view directory listings.

## Using Docker
When in your project directory on the command line, use `docker-compose build` to build this docker image.

After building, use `docker-compose up` from the project directory to run the container.

After running this image container, the web page should be visible at http://localhost:8080/ (If you're using Docker Tools because you're on Windows 7, the URL may be slightly different, perhaps http://192.168.99.100:8080/)

The file `docker-compose.yml` maps the container's port 80 (default web port) to
the host's (that's your machine's) port 8080 with the `ports` command.

The `volumes` command in `docker-compose.yml` maps the your folder `app` to the
container's `\srv\app\` folder. Changes made in one place will be made in the
 other. (Some students running Windows 7 have had issues with this step. If you're running Windows 7, but no files are showing up, try removing the `volumes` section.)

The key combo `ctrl-C` will kill the container.

## Add a `.dockerignore` File
Read the following [explanation of the `.dockerignore` file](https://blog.codeship.com/leveraging-the-dockerignore-file-to-create-smaller-images/)
Create a `.dockerignore` file with at least the following. Be able to explain what each line does.

```
.*
docker-compose.yml
*.md
```
