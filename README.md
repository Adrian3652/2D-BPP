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


       for c in cajas:
	       packer.add_rect(*c)


       for con in contenedores:
	       packer.add_bin(*con)

       packer.pack()


       ncontenedores = len(packer)


       acontenedor = packer[0]


       width, height = acontenedor.width, acontenedor.height


       ncaja = len(packer[0])


       caja = packer[0][1]


       x = caja.x # Caja inferior-izquierda coordenada x
       y = caja.y # Caja inferior-izquierda coordenada y
       w = caja.width
       h = caja.height

       for acontenedor in packer:
       print(acontenedor.bid) # Bin id if it has one
       for rect in acontenedor:
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
		
                ax.add_patch(patch)
		rx, ry = patch.get_xy()
		cx = rx + patch.get_width()/2.0
		cy = ry + patch.get_height()/2.0
		
		ax.annotate(f'w:{w}\nh:{h}', (cx, cy), color='b', weight='bold', 
					fontsize=6, ha='center', va='center')
					
	fig.savefig(f"./Panel Optimization/{abin.bid}_{bw}x{bh}_{index+1}.png", 
			    dpi=1200, 
				papertype='letter',
				bbox_inches='tight')`
