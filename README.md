# pinkprism

vibe code

## formula
```c
    vec3 dx = dFdx(vPos); // tangent x
    vec3 dy = dFdy(vPos); // tangent y
    N = normalize(cross(dx, dy)); // normal
```

## [Cg 3.1 Toolkit Documentation Cg Standard Library fwidth](https://developer.download.nvidia.com/cg/ddx.html)


Name
ddx - returns approximate partial derivative with respect to window-space X

Synopsis
float  ddx(float a);
float1 ddx(float1 a);
float2 ddx(float2 a);
float3 ddx(float3 a);
float4 ddx(float4 a);

half   ddx(half a);
half1  ddx(half1 a);
half2  ddx(half2 a);
half3  ddx(half3 a);
half4  ddx(half4 a);

fixed  ddx(fixed a);
fixed1 ddx(fixed1 a);
fixed2 ddx(fixed2 a);
fixed3 ddx(fixed3 a);
fixed4 ddx(fixed4 a);
Parameters
a
Vector or scalar of which to approximate the partial derivative with respect to window-space X.
Description
Returns approximate partial derivative of a with respect to the window-space (horizontal) x coordinate.

For vectors, the returned vector contains the **approximate partial derivative** of each element of the input vector.

This function is only available in fragment program profiles (but not all of them).

The specific way the **?partial derivative** is computed is implementation-dependent. Typically fragments are rasterized in **2x2** arrangements of fragments (called quad-fragments) and the partial derivatives of a variable is computed by <span style="color:red"> **differencing** </span> with the adjacent horizontal fragment in the quad-fragment.

The partial derivative computation may incorrect when ddx is used in control flow paths where not all the fragments within a quad-fragment have branched the same way.

The partial derivative computation may be **less exact** (wobbly) when the variable is computed based on varying parameters **interpolated** with centroid interpolation.