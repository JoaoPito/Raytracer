Each ray that hits a diffuse material is reflected in a random angle each time, we call this effect **scattering**.

When we calculate the bounced ray, we need to calculate these properties:
- The direction of the ray
- The color of the material
- The % of color of the previous ray mixed with the new calculated color

There are multiple ways to calculate the scattered ray direction. Here we implemented 3 methods, although we later replaced each individual method with a dedicated diffuse material:

- [[Rejection Method Reflections]]
- [[Lambertian Reflections]]
- [[Hemisphere Reflections]]
