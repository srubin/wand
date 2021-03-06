Roadmap
=======

Version 0.3
-----------

Drawing (:issue:`64`)
   Wand 0.3 will provide drawing facilities of ImageMagick.

   Adrian Jung did the the most of it (:issue:`64`).

   It's been working on :branch:`drawing` branch.

Sequences (:issue:`34`, :issue:`39`, :issue:`66`)
   Wand 0.3 will be able to deal with sequences.  For example, ICO format
   can contain multiple sizes of images in a file, Wand 0.3 can work with
   it.

   Michael Elovskikh had done the most of works for it (:issue:`39`) and
   Andrey Antukh also suggested an alternative improved API (:issue:`66`)
   for it.

   The branch name for it will be :branch:`sequence`.

EXIF (:issue:`56`, :issue:`25`)
   ImageMagick itself can read/write EXIF through :c:func:`GetMagickInfo`
   function.  Wand 0.3 will make a binding for it.

   It's already available on :branch:`master`.  (Worked by Michael Elovskikh.)

`Seam carving`_
   ImageMagick optionally provides seam carving (also known as liquid rescaling
   or content-aware resizing) through :c:func:`MagickLiquidRescaleImage()`
   function if it's properly configured ``--with-lqr``.

   Wand 0.3 will have a simple method :meth:`Image.liquid_rescale()
   <wand.image.Image.liquid_rescale>` method which binds this API.

   It's already available on :branch:`master` and you can see the docs
   for it as well: :ref:`seam-carving`.

Channels
   Wand 0.3 will provide channel-related APIs:

   - :attr:`Image.channel_images <wand.image.Image.channel_images>`
   - :attr:`Image.channel_depths <wand.image.Image.channel_depths>`
   - :meth:`Image.composite_channel() <wand.image.Image.composite_channel>`

   It's already available on :branch:`master`.

.. _Seam carving: http://en.wikipedia.org/wiki/Seam_carving


Version 0.4
-----------

Python 3 compatibility
   Wand 0.4 will be the first version that supports Python 3.

   The branch name for it will be :branch:`python3`.

Jython compatibility (:issue:`9`)
   Wand 0.4 will support Jython 2.7+.  Jython 2.7 is (June 2012) currently
   under alpha release, and Wand has been tested on it and fixed incompatible
   things.

   It has been developed in the branch :branch:`jython`.

Image layers (:issue:`22`)
   Wand 0.4 will be able to deal with layers of an image.

   Its branch name will be :branch:`layer`.


Very future versions
--------------------

Animations (:issue:`1`)
   Wand will finally support animations like GIF and SWF in the future.

   Its branch name will be :branch:`animation`.

PIL compatibility layer
   PIL has very long history and the most of Python projects still
   depend on it.  We will work on PIL compatiblity layer using Wand.
   It will provide two ways to emulate PIL:

   - Module-level compatibility which can be used by changing
     :keyword:`import`::

         try:
             from wand.pilcompat import Image
         except ImportError:
             from PIL import Image

   - Global monkeypatcher which changes :attr:`sys.modules`::

         from wand.pilcompat.monkey import patch; patch()
         import PIL.Image  # it imports wand.pilcompat.Image module

CLI (:program:`covert` command) to Wand compiler (:issue:`100`)
   Primary interface of ImageMagick is :program:`convert` command.
   It provides a small *parameter language*, and many answers on the Web
   contain code using this.  The problem is that you can't simply
   copy-and-paste these code to utilize Wand.

   This feature is to make these CLI codes possible to be used with Wand.

Supporting :meth:`__array_interface__` for NumPy (:issue:`65`)
   It makes :func:`numpy.asarray()` able to take :class:`~wand.image.Image`
   object to deal with its pixels as matrix.

   Its branch name will be :branch:`numpy`.
