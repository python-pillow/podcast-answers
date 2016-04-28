Podcast.__init__ Interview
==========================

Gathering questions and answers for Podcast.__init__ interview scheduled for tonight @ 8 EDT. I'm going to add questions and answers here and create issues for questions that may require discussion. Pillow Team members and community are welcome and encouraged to add comments to help improve answers (where applicable).

How did you get introduced to Python?
-------------------------------------

In the early 2000s I was working at the National Institutes of Health in Bethesda, MD, USA (NIH) as a System Administrator and my group needed a website. A neighboring group was using `Plone <http://plone.com>`_ and I decided to copy their approach. Plone is written in Python & built on top various `Zope <https://en.wikipedia.org/wiki/Zope>`_ technologies written in Python & C. To customize Plone, you had to know a little Python, so that was my introduction. (Incidentally, that site is still running: https://afni.nimh.nih.gov/.)

What were you working on that led you to forking the Python Image Library (PIL)
-------------------------------------------------------------------------------

By the mid-2000s, I had quit my job at NIH to do Plone consulting fulltime. In 2010, I was doing Django consulting at National Geographic in DC and I remember coming in the next day and saying "I forked PIL last night." My colleagues' reaction was **yawn** and rightfully so, because no one thought about what Pillow could become, including me. I created the fork because I was annoyed with my inability to install PIL from PyPI. The PIL package was hosted off site; worse, it had flaws no one was willing or able to address upstream. This led to the proliferation of (what I felt to be annoying and inelegant) forks not hosted on PyPI e.g.:

- http://dist.plone.org/thirdparty/PIL-1.1.7.tar.gz
- http://dist.plone.org/thirdparty/PILwoTk-1.1.6.4.tar.gz

So I thought, if we're going to use these forks, let's just "go all-in" and publish the fork to PyPI. So that's what I did. Incidentally, the fork was based on work done by a "Plone guy" (at the time) named Hanno Schlicting. He address one major annoyance at the time (with namespace collision)::

    import Image

With Hanno's PIL, it was only possible to import Image from PIL::

    from PIL import Image

At the time, I called Pillow "a packaging fork".

What does Fredrik Lundh (author of PIL) think of Pillow?
--------------------------------------------------------

My favorite story to tell about Fredrik involves a comment he made in response to `my introduction to Pillow on image-sig <https://mail.python.org/pipermail/image-sig/2010-July/006423.html>`_. He said something like "A lot of people complain; at least someone is doing something about it." Or at least that's how I choose to interpret his comment. His exact words (and more context) are here:

- https://mail.python.org/pipermail/image-sig/2010-August/006429.html

When you first forked the PIL project did you think that you would still be maintaining and updating that fork by now?
----------------------------------------------------------------------------------------------------------------------

No. I didn't think about it at all. I just knew that my Plone installations were going to be awesome. When Pillow caught on, I was really happy others found it useful. Now-a-days, most of the day to day operations of Pillow development are performed by the `Pillow Team <https://github.com/orgs/python-pillow/people>`_ and `global community <https://github.com/python-pillow/Pillow/graphs/contributors>`_ without my intervention. I pop in about once per quarter to make sure releases go according to plan, and to prune repositories and issues. Additionally, I just registered python-pillow.org so we could ensure that security-related emails make it to the right members of the team.

Can you describe what PIL and now Pillow are and what kinds of use cases they support?
--------------------------------------------------------------------------------------

Sure. PIL allows Python programmers to `perform complex image manipulation operations <http://docs.python-guide.org/en/latest/scenarios/imaging/#example>`_ without having to know the details and algorithms involved in performing such operations, e.g.:

- Viewing EXIF data embedded in image
- Splitting the image into its respective bands, i.e. Red, Green, and Blue for RGB
- Applying a filter to the image

As a Python Web Developer, I use Pillow to manipulate images in my web applications. In some cases, that manipulation is seemless (i.e. the image manipulation code is already written; e.g. Plone uses Pillow to enable content editors to manipulate images on their website). In other cases, I write Pillow code to perform some manipulation that is needed in my application (e.g. create thumbnails).

Discussion
~~~~~~~~~~

- `Can you describe what PIL and now Pillow are and what kinds of use cases they support? <https://github.com/python-pillow/podcast-answers/issues/1>`_

.. raw:: html

    <hr>

What architectural patterns does Pillow use to make image operations fast and flexible? Have you found the need to do any significant refactorings of the original code to make it compatible with modern uses and execution environments?
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

PIL has about 30K lines of C code, which contain various modules for imaging manipulation, that are `made available from Python via C Extensions <https://docs.python.org/2/extending/extending.html>`_. The biggest refactor was probably when we added Python 3 compatibility. That's when we really started changing things, and Pillow became more than just a packaging fork.

Discussion
~~~~~~~~~~

- `What architectural patterns does Pillow use to make image operations fast and flexible? Have you found the need to do any significant refactorings of the original code to make it compatible with modern uses and execution environments? <https://github.com/python-pillow/podcast-answers/issues/2>`_

.. raw:: html

    <hr>
