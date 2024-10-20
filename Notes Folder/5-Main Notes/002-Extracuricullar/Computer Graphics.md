---
Status: In Progress
Date: 2024-10-06T22:49
---


2024-09-06 18:52

Tags:


# Computer Graphics

### Forward Ray Tracing: 

Photons emitted by light source impact the pixels on the plane once the pixels by incrementally brightening them once the pixels are properly adjusted we get a computer generated image

**Disadvantages:**

This method assumes that each pixel will properly meet the eye however that is not the case even in real world we have thousand of photons moving at the speed of light scattering around thus we are able to see properly 

To optimise it we direct the photons to the eyes of the user since we know the approximate location this is an optimisation problem in this field

### Backward Ray Tracing or Path Tracing

Here we initiate the light from our eyes and then make it reflect from the object to the light source. 
We send another ray which if collided with the object the first ray becomes the shadow ray the first ray is called as primary, visibility, camera ray and the second ray becomes the shadow ray

In this image the shadow ray is not blocked by anything so the area has no shadows
![[ray_tracing.png]]

The shadow ray has been blocked by another object therefore we can assume that there is a shadow forming on area we release multiple lines like this to get as clear a shadow as possible therefore i think that this is what causes an increase in the cpu load when increasing the graphics in a game 

![[ray_tracing_back.png]]


```pseudocode
for (int j = 0; j < imageHeight; ++j) { 
    for (int i = 0; i < imageWidth; ++i) { 
        // Determine the direction of the primary ray
        Ray primRay; 
        computePrimRay(i, j, &primRay); 
        // Initiate a search for intersections within the scene
        Point pHit; 
        Normal nHit; 
        float minDist = INFINITY; 
        Object *object = NULL; 
        for (int k = 0; k < objects.size(); ++k) { 
            if (Intersect(objects[k], primRay, &pHit, &nHit)) { 
                float distance = Distance(eyePosition, pHit); 
                if (distance < minDist) { 
                    object = &objects[k]; 
                    minDist = distance;  // Update the minimum distance
                } 
            } 
        } 
        if (object != NULL) { 
            // Illuminate the intersection point
            Ray shadowRay; 
            shadowRay.direction = lightPosition - pHit; 
            bool isInShadow = false; 
            for (int k = 0; k < objects.size(); ++k) { 
                if (Intersect(objects[k], shadowRay)) { 
                    isInShadow = true; 
                    break; 
                } 
            } 
        } 
        if (!isInShadow) 
            pixels[i][j] = object->color * light.brightness; 
        else 
            pixels[i][j] = 0; 
    } 
}
```

However the downside of ray tracing is that this technique is divided into 2 phases 
1. Visibility determination
2. Shading

Both of these techniques are computationally taxing and therefore this stops it from being one of the most simplest and efficient method of image generation

The Ray tracing method was then updated to add advanced optical effects like reflection and refraction

![[reflection_refraction_ray.png]]

To calculate reflection and refraction we need to make 2 calculations
1. Reflection Calculations
	1. The first involves calculating the direction of the light to do that we need
		1. The surface normal at the point of intersection
		2. The incoming direction of the primary ray
	2. We then use another algorithm to calculate how much light will be transmitted we do this by sending a shadow ray which will then turn the color to black if its a shadow. 
2. Refraction Calculations
	1.  We pass another ray through the object known as the transmission ray  to calculate its direction we need 
		1. The surface normal at the point of intersection
		2. The incoming direction of the primary ray
		3. Refractive index of the material
	2. When the ray exits the object we will bend it once more using the above mentioned parameters this shows another distortion. If the refracted ray then collides with another object then we will take its colour and adjust the final colour based on that
3. Applying the Fresnel Equation to check how much should refractive and reflective index should affect the final result

```pseudocode
// compute reflection color
color reflectionColor = computeReflectionColor(); 

// compute refraction color
color refractionColor = computeRefractionColor(); 

float Kr; // reflection mix value
float Kt; // refraction mix value

// Calculate the mixing values using the Fresnel equation
fresnel(refractiveIndex, normalHit, primaryRayDirection, &Kr, &Kt);

// Mix the reflection and refraction colors based on the Fresnel equation. Note Kt = 1 - Kr
glassBallColorAtHit = Kr * reflectionColor + Kt * refractionColor;
```


# References
---


	