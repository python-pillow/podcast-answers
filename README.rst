Podcast.__init__ Interview
==========================

Gathering questions and answers for Podcast.__init__ interview scheduled for tonight @ 8 EDT. I'm going to add questions and answers here and create issues for questions that may require discussion. Pillow Team members and community are welcome and encouraged to add comments to help improve answers (where applicable).

How did you get introduced to Python?
-------------------------------------

In the early 2000s I was working at the National Institutes of Health in Bethesda, MD, USA (NIH) as a System Administrator and my group needed a website. A neighboring group was using `Plone <http://plone.com>`_ and I decided to copy their approach. Plone is written in Python & built on top various `Zope <https://en.wikipedia.org/wiki/Zope>`_ technologies written in Python & C. To customize Plone, you had to know a little Python, so that was my introduction. (Incidentally, that site is still running: https://afni.nimh.nih.gov/.)

What were you working on that led you to forking the Python Image Library (PIL)
-------------------------------------------------------------------------------

By the mid-2000s, I had quit my job at NIH to do Plone consulting fulltime. In 2010, I was doing Django consulting at National Geographic in DC and I remember coming in the next day and saying "I forked PIL last night." My colleagues' reaction was **yawn** and rightfully so, because no one thought about what Pillow could become, including me. I created the fork because I was annoyed with my inability to install PIL from PyPI. The PIL package was hosted off site; worse, it had flaws no one was able to address upstream. This led to the proliferation of (what I felt to be annoying and inelegant) forks not hosted on PyPI e.g.:

- http://dist.plone.org/thirdparty/PIL-1.1.7.tar.gz
- http://dist.plone.org/thirdparty/PILwoTk-1.1.6.4.tar.gz

So I thought, if we're going to use these forks, let's just "go all-in" and publish the fork to PyPI. So that's what I did. Incidentally, the fork was based on work done by a "Plone guy" (at the time) named Hanno Schlicting. He address one major annoyance at the time (with namespace collision)::

    import Image

With Hanno's PIL, it was only possible to import Image from PIL::

    from PIL import Image

What does Fredrik Lundh (author of PIL) think of Pillow?
--------------------------------------------------------

My favorite story to tell about Fredrik involves a comment he made in response to `my introduction to Pillow on image-sig <https://mail.python.org/pipermail/image-sig/2010-July/006423.html>`_. He said something like "A lot of people complain; at least someone is doing something about it." Or at least that's how I choose to interpret his comment. His exact words (and more context) are here:

- https://mail.python.org/pipermail/image-sig/2010-August/006429.html
