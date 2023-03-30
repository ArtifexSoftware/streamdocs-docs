.. Copyright (C) 2001-2023 Artifex Software, Inc.
.. All Rights Reserved.

.. meta::
   :description: StreamDocs Online documentation
   :keywords: StreamDocs, doc, xls, pdf, ppt, docx, xlsx, pptx

.. include:: header.rst

Documents and the DOM
===============================


This section describes how documents are inserted into your webpage, how the DOM_ is manipulated and what objects are created.


Your Target DIV
------------------

When you define the target `div` we recommend that it is a dedicated empty `div` for the document view. This is because when we invoke `sdo.load()` on the target then a :title:`StreamDocs` :title:`iFrame` will be appended as a child of the target `div`.

So for example, consider the following code:


.. raw:: html

   <pre>
     <code class="language-javascript" data-prismjs-copy="Copy">
       &lt;div id="sdo-view"&gt;&lt;/div&gt;
       &lt;script&gt;
         document.addEventListener('sdo.ready', function() {
           const sdo = new SDO({ apiKey: 'your_api_key', targetId: 'sdo-view' });
           sdo.load('input_pdf_url');
         });
       &lt;/script&gt;
       &lt;script src="https://dashboard.streamdocs.io/adapter.js"&gt;&lt;/script&gt;
     </code>
   </pre>

The DOM will then output:

.. raw:: html

   <pre>
      <code class="language-html" data-prismjs-copy="Copy">
         &lt;div id="sdo-view"&gt;
            &lt;iframe src="https://dashboard.streamdocs.io/view/6305ca34-5e5b-4518-a855-4870ce91ccac" style="width: 100%; height: 100%; border: none;"&gt;
            &lt;/iframe&gt;
         &lt;/div&gt;
      </code>

   </pre>




If at a later time, you then again invoke:

.. raw:: html

   <pre>
     <code class="language-javascript" data-prismjs-copy="Copy">
         sdo.load('input_pdf_url');
      </code>
   </pre>

Then in the :title:`DOM` you will see a duplication:


.. raw:: html

   <pre>
      <code class="language-html" data-prismjs-copy="Copy">
         &lt;div id="sdo-view"&gt;
            &lt;iframe src="https://dashboard.streamdocs.io/view/6305ca34-5e5b-4518-a855-4870ce91ccac" style="width: 100%; height: 100%; border: none;"&gt;
            &lt;/iframe&gt;

            &lt;iframe src="https://dashboard.streamdocs.io/view/6305ca34-5e5b-4518-a855-4870ce91ccac" style="width: 100%; height: 100%; border: none;"&gt;
            &lt;/iframe&gt;

         &lt;/div&gt;
      </code>

   </pre>

Note, this is by design!

:title:`StreamDocs` does not assume how you might want to manipulate your :title:`DOM` it just inserts `iFrame` constructs which contains your :title:`PDF`.

It is very likely that you may want to use the same `div` for different documents, in this case you should empty the target `div` of its children before continuing.

For example:

.. raw:: html

   <pre>
      <code class="language-javascript" data-prismjs-copy="Copy">
         document.getElementById("sdo-view").innerHTML = "";
      </code>
   </pre>

Now with an empty `div`, you can load another document into the target and it will contain just the single `iFrame` with you may expect.

.. External links



.. _DOM: https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model




.. include:: footer.rst
