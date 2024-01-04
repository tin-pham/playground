# Anti-Aliasing

- Caused by samplingrates are less than twice the frequency

- To achive anti-aliasing:
  ⋅⋅- Higher the resolution
  ⋅⋅- Increase the sample rate (MSAA, SSAA, EQAA, CSAA)
  ⋅⋅- Blur the edges/contrasts (aka Post-AA or Post-Processing) (FXAA, MLAA, SMAA)

## Chart

- Performance from least to most demanding:

```
Off > MLAA/FXAA = SMAA >>> MSAA => EQAA/CSAA >= TXAA >>> SSAA > TXAA using SSAA
```

- Blur/sharpness from sharpest to blurest

```
SSAA > MSAA=EQAA/CSAA=Off >>> SMAA > TXAA > FXAA/MLAA >>> TXAA

```

- Reduce jaggies from best to worst

```
TXAA > SMAA=MLAA/FXAA >= SSAA > EQAA/CSAA > MSAA (on polygon edges)=MSAA (with coverage 2 alpha) >>> MSAA (on alpha textures)=Off
```

## SSAA (Super Sampling Anti-Aliasing) - aka FSAA (Full Scene Anti-Aliasing)

- It increase the sample rate [^1]
- Best looking form of AA, since the textures get sharper
- Very costly [^2]

[^1]: To render the scene at higher resolution, for each pixel of image, it will output x2, x4, x8 pixel depend on setting
[^2]: If the game run at 4K, with SSAAx4, it will 4 time 4K => 8K, the 8K image is running on 4K monitor

## MSAA (Multi Sampling Anti-Aliasing)

- Optimize version of SSAA, since it only increase the sample rate at the edges
- It can cause jaggy effect on complex geometry textures like grass

## EQAA (Enhanced Quality Anti-Aliasing) and CSAA (Coverage Sample Anti-Aliasing)

- Try to increase quality of MSAA

## MLAA (Morphological Anti-Aliasing) and FXAA (Fast Approximate Anti-Aliasing)

- Finding edges after the scene have been rendered, then blur it => Fast
- Highly reduces "jaggies", but it blur everything
- Cheapest form of AA

## SMAA (Subpixel Morphological Anti-Aliasing)

- Base on Post-AA like MLAA, FXAA but image is closer to SSAA => Cheap and doesn't blur image much
- Best AA based on community

## TXAA (Temporal Anti-Aliasing)

- Complex form of AA, it's not Post-AA
- The reducement of "jaggies" is one of the best of all AA
- Use more performance than MLAA, FXAA
- It blur even more than MLAA, FXAA [^1]

[^1]: If you run the game at high resolution (4K), it might be acceptable
