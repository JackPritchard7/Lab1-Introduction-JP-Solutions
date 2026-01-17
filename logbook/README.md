# Lab 1 – Introduction to MATLAB - Logbook - 17/01/26

## Task 1 – Rotation (Reverse Mapping)
- Implemented `Rotate(In, Theta)` using a 2×2 rotation matrix:
  - Converted input angle from degrees to radians (`Theta = deg2rad(Theta)`).
  - Computed inverse transform (`itm = inv(tm)`) for reverse mapping to avoid holes from forward mapping.
  - Rotated about the image centre using `cp = [rows/2; cols/2]`.
  - For each destination pixel `p = [r; c]`, computed source coordinate `tp = itm*(p-cp)+cp`.
  - Applied nearest-neighbour sampling with `rs = round(tp(1))`, `cs = round(tp(2))`.
  - Out-of-bounds source locations were painted black (`Out(r,c)=0`).

## Task 2 – Shearing (Reverse Mapping)
- Implemented `Shear(In, xshear, yshear)` using the shear matrix:
  - `tm = [1 xshear; yshear 1]`, with reverse mapping via `itm = inv(tm)`.
  - Used the same centre-point approach (`cp = [rows/2; cols/2]`) so the centre pixel remains stationary.
  - For each destination pixel, mapped back to the source using `tp = itm*(p-cp)+cp`.
  - Used nearest neighbour (`round`) and black padding for out-of-bounds pixels.
