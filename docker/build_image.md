# Build image
> **Lien Chen** *2024-01-04*

* Before we use *docker build --no-cache --tag mongo7 .* an example code to create image
But current this usage became deprecated.
We need to change it to be buildx build to build the image.
*docker build --no-cache --tag mongo7 .* => *docker buildx build --no-cache --tag mongo7 .*