---
title: What is optical character recognition (OCR)?
source: https://www.ibm.com/think/topics/optical-character-recognition
author:
- '[[Jim Holdsworth]]'
published: 2024-11-27
created: 2026-08-31
description: "Optical character recognition saves time, cost and other resources by utilizing automated data extraction and storage capabilities."
---

## What is OCR?

Optical character recognition (OCR) is a technology that uses automated data extraction to quickly convert images of text into a machine-readable format.

OCR is sometimes referred to as text recognition. An OCR program extracts and repurposes data from scanned documents, camera images and image-only PDFs. OCR software singles out letters on the image, puts them into words, and then puts the words into sentences, thus enabling access to and editing of the original content. It also eliminates the wasted effort of redundant manual data entry.

OCR systems use a combination of hardware and software to convert physical, printed documents into machine-readable text. Hardware, such as an optical scanner or specialized circuit board, copies or reads text, then software typically handles the advanced processing.

OCR software can take advantage of [artificial intelligence (AI)](https://www.ibm.com/think/topics/artificial-intelligence) to implement more advanced methods of intelligent character recognition (ICR) for identifying languages or handwriting. Organizations often use the process of OCR to turn printed legal or historical documents into PDF documents so that users can edit, format and search the documents as if created with a word processor.

## The history of OCR

In 1974, Ray Kurzweil started Kurzweil Computer Products, Inc., whose omni-font OCR product might recognize text printed in virtually any font. He decided that the best application of this technology would be a [machine learning](https://www.ibm.com/think/topics/machine-learning) (ML) device for the vision-impaired, so he created a reading machine that might read text aloud in a text-to-speech format. In 1980, Kurzweil sold his company to Xerox, which was interested in further commercializing paper-to-computer text conversion.

OCR technology became popular in the early 1990s while digitizing historical newspapers. Since then, the technology has undergone several improvements. Today, products can deliver near-to-perfect OCR accuracy. Advanced methods can automate complex [document-processing workflows](https://www.ibm.com/think/topics/document-processing).

Before OCR technology became available, the only option to digitally format documents was manually reentering the text. Not only is the redundant input time-consuming, but it also comes with inevitable inaccuracies and typing errors. Today, OCR services are widely available to the public. For example, Google Cloud Vision OCR can be used to scan and store documents on your smartphone.

## How does OCR work?

OCR software uses a scanner to reprocess the physical form of a document to editable, digital text. The OCR software can run as a free-standing program, OCR application programming interface or web-based service.  

 **Image acquisition:** All document pages are copied and then the OCR engine converts the digital document into a two-color or black-and-white version. The scanned-in image or bitmap is analyzed for light and dark portions. The program then identifies the dark portions as characters that need to be recognized, while light areas are identified as background.

**Preprocessing:** The digital image is cleaned to remove extraneous pixels. This preprocessing can include deskewing to correct for the image being improperly aligned during scanning, removing graphic rules and boxes that were part of the printed image and determining whether script text is included.

**Text recognition:** The dark portions are processed to find alphabetic letters, numeric digits or symbols. This stage typically involves targeting one character, word or block of text at a time. Characters are then identified by using one of two algorithms, either pattern recognition or feature recognition.

- Pattern recognition (or pattern matching): The OCR program has previously been trained on examples of text in various fonts and formats to recognize characters by comparison to a template in the scanned document or image file. Each unique combination of shape, scale and font is called a glyph. For this to work, the characters must be in a font that the OCR program has already been trained on. Given the number of fonts worldwide and languages that use different characters, such as Arabic, Chinese, English, French, German, Greek, Japanese, Korean or Spanish, training on every combination of font and language would be an enormous system drain.
- Feature recognition (detection or extraction): This is used when the OCR program is analyzing a font that it has not been trained on. OCR applies rules regarding the features of a specific letter or number to recognize characters in the scanned document. Features include the number of angled lines, line intersections, loops or curves in a character. For example, the capital letter “A” is stored as two diagonal lines that meet with a horizontal line across the middle. When a character is identified, it is converted into an American Standard Code for Information Interchange (ASCII) code that computer systems use to handle further manipulations.

**Layout recognition:** A more complete OCR program will also analyze the structure of a document image. It divides the page into elements, such as blocks of text, tables or images. The lines are divided into words and then into characters. After the characters have been singled out, the program compares them with a set of pattern images. After processing all likely matches, the program returns the recognized text.

**Postprocessing:** The gathered information is stored as a digital file, either in an editable form or PDF. Some systems retain both the input image and the post-OCR versions for easier comparison and more complete [document management](https://www.ibm.com/think/topics/document-management).

## Types of OCR

There are 4 types of OCR programs, with increasing sophistication:

**Simple OCR:** Analysis is character-by-character pattern-matching, comparing scanned characters to the stored glyphs. With so many potential font and language combinations, the types of documents that can be analyzed are limited.

**Optical mark recognition (OMR):** For identifying checked boxes and [other marks](https://www.ibm.com/docs/en/datacap/9.1.9?topic=overview-datacap-functional), such as bubbles in surveys or a signature on a form, plus logos, symbols and watermarks. All can be identified by matching to stored images, as with simple OCR.  

 **Intelligent character recognition (ICR):** As mentioned previously, ICR brings in the power of AI. By using [ML](https://www.ibm.com/think/topics/machine-learning) or [deep learning](https://www.ibm.com/think/topics/deep-learning), the OCR program learns to read just as humans do: through continual practice and training. A neural network reviews text repeatedly looking for distinctive attributes: the locations of curves, intersections, lines and loops.

**Intelligent word recognition:** This is the natural evolution of the previous ICR recognition, but now the AI has been trained to recognize a word in a single image, making it ultimately faster.

## The benefits of OCR

The benefits of employing OCR technology include the ability to:

- Cut costs by reducing or eliminating redundant manual input.
- Streamline [workflows](https://www.ibm.com/think/topics/workflow) with the input of preprinted documents or written forms and speed research with searchable digital data.
- Automate document routing, content processing and preparation for [text mining](https://www.ibm.com/think/topics/text-mining).
- Save the cost of storing yet more paper records.
- Centralize and secure data sets for protection against fires, break-ins and documents lost in the bank vaults.
- Enable greater access to data for visually impaired staff and customers.
- Improve service by giving employees the most up-to-date and accurate information.

## OCR use cases

The most well-known use case for OCR is converting printed paper documents into machine-readable text documents. After a scanned paper document goes through OCR processing, the text of the document can be edited with a word processor such as Microsoft Word or Google Docs. Multiple use cases can accelerate workloads in many industries, including education, finance, healthcare, logistics and transportation, processing and retrieving loan documents, patient records, insurance forms, labels, invoices and receipts.

OCR is often used as a hidden technology, powering many well-known systems and services in our daily lives. Important, but less-known, use cases for OCR technology include data-entry [automation](https://www.ibm.com/think/topics/automation), assisting blind and visually impaired persons and indexing documents for search engines, such as passports, license plates, invoices, bank statements, check processing and transcription, business cards and automatic number plate recognition.

OCR enables the optimization of big-data modeling by converting paper and scanned image documents into machine-readable, searchable PDF files. Processing and retrieving valuable information requires first applying OCR in documents where text layers are not already present.

With OCR text recognition, scanned documents can be integrated into a big-data system that is then able to read client data from bank statements, contracts and other important printed documents. Instead of having employees examine countless image documents and manually feed inputs into an automated big-data processing workflow, organizations can use OCR to automate that process at the input stage of [data mining](https://www.ibm.com/think/topics/data-mining). OCR software can extract text seen in pictures, save the text file and support multiple formats, including jpg, jpeg, png, bmp, tiff and pdf.

## Latest advances in OCR

OCR has [advanced significantly](https://www.ibm.com/new/product-blog/exploring-ibms-new-optical-character-recognition-technology) past the first business systems in 1974 and progress continues. Superior OCR programs can provide extraction of key insights from documents in [suboptimal conditions](https://www.ibm.com/products/watson-discovery), such as irregular fonts, insufficient resolution, bad lighting from mobile capture and various colors and backgrounds.

By incorporating [computer vision](https://www.ibm.com/think/topics/computer-vision) and [natural language processing](https://www.ibm.com/think/topics/natural-language-processing), improved information representation and model optimization, businesses can now enjoy state-of-the-art document understanding. Improvements can include analysis of layout and reading order in complex documents understanding visuals and representing them as charts and diagrams. Some OCR programs now are driven by generative AI to help structure document data even faster. An “old” technology continues to learn new tricks.
