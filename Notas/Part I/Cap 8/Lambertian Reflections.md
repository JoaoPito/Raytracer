The Rejection Method reflections are a Lambertian Reflections but the scattered rays have a high probability of landing closer to the normal vector, this results in rays hitting at a shallow angle end up contributing less to the final color.

Lambertian Reflections implement a Lambertian Distribution, which has a more uniform distribution than the previous one, but still closer to the normal.
This is done by **picking random points *on the surface* of the normal sphere** rather than picking **inside** the normal sphere, we calculate this by picking random points inside the sphere, than we normalize them.

We implement this in the method **random_unit_vector()** in the file vec3.h.