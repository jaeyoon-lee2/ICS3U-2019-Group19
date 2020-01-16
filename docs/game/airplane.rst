.. _space_ship:

Show Airplane
==========

sprites can be placed in front of the background. xxx

.. code-block:: python
        :linenos:

        sprites = []

        plane = stage.Sprite(image_bank_1, 8, 72, 56)
        sprites.append(plane)


As soon as you save the file onto the PyBadge, the screen should flash and you should see something like:

.. figure:: ./images/show_plane.jpg
   :width: 480 px
   :alt: White background
   :align: center

   Background on PyBadg

This code will not work. The code above has a lot to do. Here is a better version that shows the background. You can see that you called the :py:func:`main()` function. This is common in python code but usually not visible in CircuitPython. I am including it because by breaking the code into different functions to match different scenes, eventually will be really helpful.

.. code-block:: python
      :linenos:

      #!/usr/bin/env python3

      # Created by : Jay Lee
      # Created on : Jan 2020
      # This program display background of pybadge

      import ugame
      import stage


      def main():
          # this function display background of pybadge
          image_bank_1 = stage.Bank.from_bmp16("avoid_or_shoot.bmp")

          background = stage.Grid(image_bank_1, 10, 8)

          sprites = []

          plane = stage.Sprite(image_bank_1, 8, 72, 56)
          sprites.append(plane)

          # create a stage for the background to show up on
          #   and set the frame rate to 60fps
          game = stage.Stage(ugame.display, 60)
          # set the layers, items show up in order
          game.layers = sprites + [background]
          # render the background and inital location of sprite list
          # most likely you will only render background once per scene
          game.render_block()

          # repeat forever, game loop
          while True:
              game.render_sprites(sprites)
              game.tick()


      if __name__ == "__main__":
          main()

Now, you can get a sprite to show up in front of your background on your PyBadge.
    