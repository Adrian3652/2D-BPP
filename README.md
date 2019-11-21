# -*- coding: utf-8 -*-
"""
Spyder Editor

This is a temporary script file.
"""

from rectpack import newPacker
from matplotlib import pyplot as plt
import matplotlib.patches as patches


cajas = [(100, 30), (40, 60), (30, 30),(70, 70), (100, 50), (30, 30)]
contenedores = [(300, 450)]

packer = newPacker()

# Agregar las cajas en la lista de empaque
for c in cajas:
	packer.add_rect(*c)

# Añadir los contenedores donde las cajas van a ubicarse
for con in contenedores:
	packer.add_bin(*con)

# Empezar a empacar
packer.pack()

# Obtener el número de contenedores usados en el empaque
ncontenedores = len(packer)

# Index del primer contenedor
acontenedor = packer[0]

# Dimensiones del Contenedor (pueden ser reordenados durante el empaque)
width, height = acontenedor.width, acontenedor.height

# Número de cajas empacados en el primer contenedor
ncaja = len(packer[0])

# Segundo contenedor, primera caja
caja = packer[0][1]

# Caja es un objeto rectángulo
x = caja.x # Caja inferior-izquierda coordenada x
y = caja.y # Caja inferior-izquierda coordenada y
w = caja.width
h = caja.height

for abin in packer:
  print(abin.bid) # Bin id if it has one
  for rect in abin:
    print(rect)

for index, acontenedor in enumerate(packer):
  bw, bh  = acontenedor.width, acontenedor.height
  print('contenedor', bw, bh, "nr of rectangles in bin", len(acontenedor))
  fig = plt.figure(figsize=(12,8))
  ax = fig.add_subplot(111, aspect='equal')
  for rect in acontenedor:
    x, y, w, h = caja.x, caja.y, caja.width, caja.height
    plt.axis([0,bw,0,bh])
    print('rectangle', w,h)
    ax.add_patch(
        patches.Rectangle(
            (caja.x, caja.y),  # (x,y)
            w = (caja.width),          # width
            h = (h),          # height
            facecolor="#00ffff",
            edgecolor="black",
            linewidth=3
        )
    )
  fig.savefig("rect_%(index)s.png" % locals(), dpi=144, bbox_inches='tight')
		# add the patch and get it's center
		ax.add_patch(patch)
		rx, ry = patch.get_xy()
		cx = rx + patch.get_width()/2.0
		cy = ry + patch.get_height()/2.0
		
		# drop anno in the center with width and height.
		ax.annotate(f'w:{w}\nh:{h}', (cx, cy), color='b', weight='bold', 
					fontsize=6, ha='center', va='center')
					
	fig.savefig(f"./Panel Optimization/{abin.bid}_{bw}x{bh}_{index+1}.png", 
			    dpi=1200, 
				papertype='letter',
				bbox_inches='tight')`
