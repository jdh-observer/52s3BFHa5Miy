---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.16.6
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

<!-- #region tags=["title"] -->
# Voyages in 3D: Creating a Multimodal Narrative of the Battle of Mount Street Bridge

<!-- #endregion -->

<!-- #region tags=["keywords"] -->
Digital Storytelling, 3D Narrative, 3D Web Viewer, Intermediality
<!-- #endregion -->

<!-- #region tags=["abstract"] -->
Contested Memories: The Battle of Mount Street Bridge (BMSB) is a long-term research project that utilises 3D technologies to explore one of the key battles of the Easter 1916 Rising in Dublin, a week-long insurrection with the goal of attaining Irish independence from Great Britain. Begun in 2013, the project was designed to answer a specific research question: how many casualties did the British troops sent to quell the insurrection suffer during the battle. The BMSB team met its goal which was reported in the Journal of British Military History. Yet, we were dissatisfied with the research team being the only ones who were able to gain insights from the 3D models created, as typically is the case with so much 3D scholarship. Thus in 2021 PURE3D was funded to develop an infrastructure for the publication and preservation of scholarship created in 3D, with the BMSB a key source for developing the infrastructure. PURE3D has adopted Voyager Story as one of its 3D viewers, and the BMSB team has utilised it to create an intermedial multimodal publication of the battle.

Voyager Story, an open-source 3D viewer developed by the Smithsonian Institution, combines textual, visual, moving images and audio to create a rich environment for creating a (spatial) narrative, with a 3D model the central navigational and narrative pillar. Voyager Story also provides for hotspot annotation labels on the 3D model, accompanied by short descriptions. From an annotation label, longer ‘articles’ can be expanded to display supporting digital content, including text, image, hyperlinks, audio, video and other types of embeddable media (including other 3D models). Multiple guided tours can then be created in which camera movements, 3D scene changes, annotation labels, and articles are flexibly organized for designing engagement between the model and the accompanying narrative.

Due to the software design, the MountStreet Bridge team decided to not treat the entire view of the battle as a whole within the software, but rather to present each building separately, creating a linked-spatial narrative of the battle. The first building to be treated this way, 25 Northumberland Road was the first building where the British encountered resistance from Irish troops on 26 April 1916 during their march from the port of Kingstown into Dublin’s city centre.

In the process of developing 25 Northumberland Road within Voyager, conceptual challenges emerged that are not found with other forms of media publication. It is our contention that as opportunities open up for 3D-centred publication to become part of the digital heritage ecosystem, further critical analysis is needed on the practical implications of these applications as communication media. This article will explore these challenges and opportunities, both for utilising 3D generally, and Smithsonian Voyager specifically, to construct historical narratives, particularly (but not exclusively) for a public audience. This implementation has also had significant feedback, in the form of an online survey and focus group, the findings of which will also be reported.

<!-- #endregion -->

## Introduction

<!-- #region citation-manager={"citations": {"cite2c-8908013/82J996JW": [{"id": "8908013/82J996JW", "source": "cite2c"}], "cite2c-8908013/89VC2TCG": [{"id": "8908013/89VC2TCG", "source": "cite2c"}], "cite2c-8908013/BAII7R6W": [{"id": "8908013/BAII7R6W", "source": "cite2c"}], "cite2c-8908013/BUBQVEB5": [{"id": "8908013/BUBQVEB5", "source": "cite2c"}], "cite2c-8908013/IAEF8FZJ": [{"id": "8908013/IAEF8FZJ", "source": "cite2c"}], "cite2c-8908013/IZ2MULJL": [{"id": "8908013/IZ2MULJL", "source": "cite2c"}], "cite2c-8908013/JWJAWNDI": [{"id": "8908013/JWJAWNDI", "source": "cite2c"}], "cite2c-8908013/KLAI2PHI": [{"id": "8908013/KLAI2PHI", "source": "cite2c"}], "cite2c-8908013/W2SWNKI9": [{"id": "8908013/W2SWNKI9", "source": "cite2c"}], "cite2c-8908013/WCRAPGXY": [{"id": "8908013/WCRAPGXY", "source": "cite2c"}], "cite2c-8908013/XJS9FEZW": [{"id": "8908013/XJS9FEZW", "source": "cite2c"}], "cite2c-8908013/ZM76CXPD": [{"id": "8908013/ZM76CXPD", "source": "cite2c"}]}} -->
The use of 3D models has long been used in fields such as history, archaeology and architecture to better understand and communicate about the past (e.g., [The War Poet’s Exhibition](http://ww1lit.nsms.ox.ac.uk/ww1lit/secondlife)) or test hypotheses of, for example, building construction (e.g., <cite id="cite2c-8908013/IAEF8FZJ"><a href="#cite2c%7C8908013%2FIAEF8FZJ">(Gruber &#38; Dobbins, 2013)</a></cite>), light sources (e.g., <cite id="cite2c-8908013/ZM76CXPD"><a href="#cite2c%7C8908013%2FZM76CXPD">(Dawson et al., 2007)</a></cite>), or visibility (e.g., <cite id="cite2c-8908013/KLAI2PHI"><a href="#cite2c%7C8908013%2FKLAI2PHI">(Paliou et al., 2011)</a></cite>). This is done by digitally (re)constructing historical structures: from cities to buildings to individual objects and even human actors (e.g., <cite id="cite2c-8908013/IZ2MULJL"><a href="#cite2c%7C8908013%2FIZ2MULJL">(Sequeira, 2020)</a></cite>). When used as an analytic tool, these models are typically not widely shared beyond the teams that utilise them, and if they are shared, it is typically as 2D images in more traditional print-based or online publications, or as video screen captures or flythroughs, often with audio narration, published on a platform like YouTube  (<cite id="cite2c-8908013/BAII7R6W"><a href="#cite2c%7C8908013%2FBAII7R6W">(Schreibman &#38; Papadopoulos, 2019)</a></cite>). While these video renderings offer more to users than 2D images, they have more in common with moving image narrative structures than academic frameworks, such as scholarly editing, which provide the user with information and annotation to aid in developing their own theories and interpretation via the interaction between the ‘text’ (in this case the 3D model) and the accompanying apparatus.

While 2D images have less capacity (compared to 3D) as a semantic for meaning-making, they can, nevertheless, be important for authors to show the results of research rather than to simply tell via prose. Thus while 2D rendered images of 3D visualisations can be compelling additions to scholarly publications, these extracted images can also be misleading.  For example, the realism and detail that can be generated using realistic texture materials and accurate lighting simulations can create an illusory nature as perfect and accurate representations of the past (<cite id="cite2c-8908013/82J996JW"><a href="#cite2c%7C8908013%2F82J996JW">(Eiteljorg, 2000)</a></cite>, <cite id="cite2c-8908013/W2SWNKI9"><a href="#cite2c%7C8908013%2FW2SWNKI9">(Clark, 2010)</a></cite>). These images may also represent only one state or version of the object (particularly over time or in the case of (re)construction), and even when accompanied by text that clarifies where, how, and to what degree the representation is accurate, as well as where the modellers have extrapolated using conjecture to fill in missing information (<cite id="cite2c-8908013/89VC2TCG"><a href="#cite2c%7C8908013%2F89VC2TCG">(Vatanen, 2003)</a></cite>, <cite id="cite2c-8908013/XJS9FEZW"><a href="#cite2c%7C8908013%2FXJS9FEZW">(Denard, 2012)</a></cite>), the powerful nature of the visual representation can make it difficult for the reader to imagine alternative scenarios or hypothesis. To counteract this, authors may provide images of several schematic models that demonstrate alternative hypotheses (e.g., <cite id="cite2c-8908013/BUBQVEB5"><a href="#cite2c%7C8908013%2FBUBQVEB5">(Papadopoulos &#38; Sakellarakis, 2013)</a></cite>, <cite id="cite2c-8908013/WCRAPGXY"><a href="#cite2c%7C8908013%2FWCRAPGXY">(Gillikin Schoueri &#38; Teixeira-Bastos, 2021)</a></cite>). However, these repetitive images can be clunky and do not allow the reader to engage with the source 3D model on which these conjectures are based. Thus  for many situations to convey scholarly arguments or hypotheses, it is preferable to make available real-time interactive 3D models to offer expanded affordances for dynamic communication. Yet, even today, although a majority of scholarly journals are available online, it is not common to embed 3D models within the article.

In an effort to address this bi-frucation of knowledge, the [Contested Memories: Battle of Mount Street Bridge Project](https://mountstreet1916.ie/)  sought to problematize the concept of 3D digital scholarly editions (<cite id="cite2c-8908013/BAII7R6W"><a href="#cite2c%7C8908013%2FBAII7R6W">(Schreibman & Papadopoulos 2019)</a></cite>). The result was an information-rich virtual world of the general area where the Battle of Mount Street Bridge took place in a leafy suburb in Dublin in April 1916 (<cite id="cite2c-8908013/JWJAWNDI"><a href="#cite2c%7C8908013%2FJWJAWNDI">(Papadopoulos & Schreibman 2019)</a></cite>). This digitally (re)constructed scene was first developed in Unity and was available online through the project website. However, by autumn 2015 the Unity Web Player was no longer supported as a browser plug-in, and the virtual world is now only available as an off-line download. The authors of the project identified this as a fundamental issue for 3D scholarship and sought to address the lack of infrastructure for the publication and preservation of 3D research by developing a follow-up project called [PURE3D](https://pure3d.eu/). In 2021, PURE3D received a PDI-SSH grant to develop such an infrastructure that could allow scholars who develop 3D models to create, edit and publish 3D digital scholarly editions without the responsibility of hosting and maintaining a 3D web viewer themselves. A series of six pilot partners from Dutch-based heritage institutions were invited to work together with the PURE3D project to develop the first 3D scholarly editions.
<!-- #endregion -->

<!-- #region editable=true slideshow={"slide_type": ""} tags=["anchor-1-1-1"] -->
### Choosing Software for the Infrastructure
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"cite2c-8908013/AIMIM5RK": [{"id": "8908013/AIMIM5RK", "source": "cite2c"}]}} editable=true slideshow={"slide_type": ""} -->
The 2000s saw the development of platforms that provided direct access to 3D, such as Unity and Second Life. Scholarship in 3D for the web necessitated a significant investment of time, money and resources to develop within these platforms, with many projects becoming unusable or obsolete due to changes in web technology (such as changes in browser standards, as was the case for the [Unity Web Player](https://unity.com/releases/editor/whats-new/5.0.0) transition to the plug-in free WebGL) or the academic shift away from Second Life due to Linden Labs increase in their pricing model (<cite id="cite2c-8908013/AIMIM5RK"><a href="#cite2c%7C8908013%2FAIMIM5RK">(Vosinakis & Tsakonas 2016)</a></cite>). In the case of Unity, for 3D gaming companies, these types of updates can be readily accommodated, but for small, one-off funded 3D heritage projects, it frequently means the end of publication on the web ([Figure 1](#anchor-figure-1-*)).


<!-- #endregion -->

```python tags=["figure-1-*", "anchor-figure-1-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 1: Some 3D projects that are no longer accessible via the WWW"
            ]
        }
    }
}
display(Image("media/figure_1.jpg"), metadata=metadata)
```

A solution that many academics and heritage organisations have utilised in more recent years for making 3D models publicly available is Sketchfab – a popular online repository for sharing, buying and selling 3D models. Its popularity within the cultural heritage sector can be attributed to their free, or otherwise affordable, web-hosting service and general ease of use for uploading 3D models to the platform. Although Sketchfab provides for annotation and (limited) metadata, as well as an iframe for embedding a model into one’s own website, the interface is limited in terms of creating a scholarly narrative around an object. Thus, while creating 3D models is now within reach of many researchers, and many heritage institutions provide freely available 3D models for download, the lack of a robust annotative and narrative environment presents a significant obstacle for their use to present a scholarly argument.

Thus when PURE3D began looking for a stable viewing environment to integrate into their infrastructure, Voyager Story, developed by the Smithsonian institution, stood out as a candidate due to their rich set of features for narrating and exploring heritage-oriented 3D models, an open-source framework, robust documentation and a dedicated back-end UI for integrating and authoring 3D models. 25 Northumberland Road (25NR) from the Contested Memories Project, the first building encountered by the British soldiers during the battle of Mount Street Bridge, was the first project to be developed in Voyager to test the potential and suitability of the software for creating a digital scholarly edition.


### The Smithsonian Voyager System


Under development by the Smithsonian Digitization Program Office (DPO), Voyager is a web viewing tool for the inspection and authoring of 3D assets ([Figure 2](#anchor-figure-2-*)). The tool is composed of two viewing interfaces, the authoring interface, named Voyager Story ([Figure 4: Right](#anchor-figure-4-*)), and the viewing interface, Voyager Explorer ([Figure 4: Left](#anchor-figure-4-*)). The aim of Voyager system is to bring the [Smithsonian’s vast collection of 3D digitised objects](https://3d.si.edu/) to a wider audience by allowing web-based exploration and interaction with these digital surrogates in an immersive and engaging way.

```python tags=["figure-2-*", "anchor-figure-2-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 2: Voyager Explorer presentation of the Neil Armstrong Spacesuit (© Smithsonian)."
            ]
        }
    }
}
display(Image("media/figure_2.jpg"), metadata=metadata)
```

<!-- #region citation-manager={"citations": {"cite2c-8908013/ENVBFDPG": [{"id": "8908013/ENVBFDPG", "source": "cite2c"}], "cite2c-8908013/R3BXIBTG": [{"id": "8908013/R3BXIBTG", "source": "cite2c"}]}} -->
Previously known as Smithsonian X3D Explorer, initial development of a 3D viewer commissioned by the Smithsonian Institution was done from 2013 to 2016 in collaboration with Autodesk. This first generation  operated as a closed framework due to proprietary ownership by Autodesk (<cite id="cite2c-8908013/R3BXIBTG"><a href="#cite2c%7C8908013%2FR3BXIBTG">(Scopigno et al. 2017)</a></cite>). However, in 2017 the Smithsonian began internal development of an entire 3D pipeline (including Voyager Explorer, Voyager Story, Cook and Packrat) and since 2019 these tools have been completely open-source and freely available on Github (<cite id="cite2c-8908013/ENVBFDPG"><a href="#cite2c%7C8908013%2FENVBFDPG">(V. Rossi, personal communication, 7 September 2023)</a></cite>).
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"cite2c-8908013/QDGI6G2X": [{"id": "8908013/QDGI6G2X", "source": "cite2c"}]}} tags=["hermeneutics"] -->
Voyager Explorer differs from other similar web viewers in that it goes beyond the functionality for quality inspection of the 3D asset (e.g., zoom in/out, measurement, cross-section or visual rendering) to also focus attention on system features that highlight aspects of digital storytelling through four distinct but interconnected modalities:
1. Annotation Labels: Short, expandable hotspot text as spatially aware annotation;
2. Articles: HTML-based pages with text and multimedia that can either overlay the 3D model or be situated to the side of it;  
3. Guided Tours: A flexible combination of annotation, articles, camera movements and a set of analytic features, such as alternative material shaders, light settings measuring tape and slicer tool;
4. Audio Narration: A single audio clip that can be played at any time during the experience (<cite id="cite2c-8908013/QDGI6G2X"><a href="#cite2c%7C8908013%2FQDGI6G2X">(Smithsonian 2023)</a></cite>).

These modalities allow viewers the option of exploring a narrative both linearly and nonlinearly. The non-linear mode of exploration involves free exploration in and around the model via  annotation labels through the  ‘read more’ feather which leads them to  an ‘article’ (of approximately 250 words). This modality provides users with a non-linear path through the content. The second mode utilises guided tours as a way to provide a structured narrative by sequencing into steps a curated narrative through annotations, articles, and camera views. While the second mode follows linear narrative conventions, it is also possible that viewers interrupt the set path by exploring other annotations or articles from within the tour. They can, however, return to where they left off  by clicking the right arrow button that moves them to the next step of the tour ([Figure 3](#anchor-figure-3-*)).

<!-- #endregion -->

```python tags=["hermeneutics", "figure-3-*", "anchor-figure-3-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 3: Voyager Interface when guided tours are enabled. The lower panel has back and forth buttons for navigating the tour."
            ]
        }
    }
}
display(Image("media/figure_3.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
While in Voyager Explorer, the user is presented with a content-rich interactive environment that operates smoothly ([Figure 4: Left](#anchor-figure-4-*)). However, this seemingly simple interface hides the complexity, both technical and conceptual, of the curation processes operating behind the scenes developed via Voyager *Story* ([Figure 4: Right](#anchor-figure-4-*)).

<!-- #endregion -->

```python tags=["hermeneutics", "figure-4-*", "anchor-figure-4-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 4: Left - Voyager Explorer viewing mode for end-users; Right - Voyager Story viewing mode for editing the experience."
            ]
        }
    }
}
display(Image("media/figure_4.jpg"), metadata=metadata)
```

<!-- #region citation-manager={"citations": {"cite2c-8908013/5FHH93KT": [], "cite2c-8908013/DZ73D8R5": [], "cite2c-8908013/ENVBFDPG": [{"id": "8908013/ENVBFDPG", "source": "cite2c"}], "cite2c-8908013/QDGI6G2X": [{"id": "8908013/QDGI6G2X", "source": "cite2c"}], "cite2c-8908013/XMN4SKMM": [{"id": "8908013/XMN4SKMM", "source": "cite2c"}]}} tags=["hermeneutics"] -->
The flexibility of Voyager Story’s configurations play an integral role in guiding this process, which in turn guides the narrative structure. For example, it is possible to connect a hotspot annotation to an expanded ‘article’ which may include a longer text and multimedia. These hotspot annotations themselves can be segmented into groups via a tagging convention that would enable a user to view only certain types or categories of annotations at a time. Another decision could be that each annotation receives its own tag thereby listing all notable features individually. This design choice could be desirable in situations where there are many relevant features on a model, so many that to display them at once would overwhelm the viewer and create difficulty in reading because of overlapping labels.

As it is intended for web viewing, the ideal 3D file format that can be ingested into Voyager is gLTF/glb. Developed by the Khronos Group, this file format is also open-source and is increasingly becoming a popular choice for web-handling as it can embed geometry, physically-based rendered (PBR) texture maps, animation, and lighting (<cite id="cite2c-8908013/XMN4SKMM"><a href="#cite2c%7C8908013%2FXMN4SKMM">(Khronos Group 2023)</a></cite>). For the 3D scene file, Voyager uses its own JSON file format (Voyager SVX Documents) which records in both machine and human-readable code configurations and commands while creating in Voyager Story (<cite id="cite2c-8908013/QDGI6G2X"><a href="#cite2c%7C8908013%2FQDGI6G2X">(Smithsonian 2023)</a></cite>). The SVX scene file was created as a way to standardise the scene data, making it easier to migrate a project into future generations of Voyager or into a completely new platform (<cite id="cite2c-8908013/ENVBFDPG"><a href="#cite2c%7C8908013%2FENVBFDPG">(V. Rossi, personal communication, 7 September 2023)</a></cite>). The Smithsonian development team is also working to make Voyager IIIF compliant. [IIIF](https://iiif.io/) (International Image Interoperability Framework)  is an organisation that establishes online standards for digital media. They have expanded their scope beyond 2D digital content to extend existing IIIF specifications to include requirements for the display of 3D media and related metadata (<cite id="cite2c-8908013/DZ73D8R5"><a href="#cite2c%7C8908013%2FDZ73D8R5">(IIIF 2024)</a></cite>). Once these 3D IIIF specifications are complete, Voyager will be able to load models and the included 3D scene information – from a IIIF manifest as well as the Voyager SVX scene file (<cite id="cite2c-8908013/5FHH93KT"><a href="#cite2c%7C8908013%2F5FHH93KT">(J. Cope, personal communication, 16 July 2024)</a></cite>).

While setting up the Voyager System for one’s organisation requires the skills of a web developer, it is possible to use [Voyager Standalone](https://3d.si.edu/voyager-story-standalone) hosted by the Smithsonian. Standalone offers the ability to set up and generate a Voyager experience within a web browser. The interaction settings can then be downloaded as a zip file containing the 3D model and a JSON file. However, to save and deploy a Voyager presentation online it is required that there is some form of secured online file storage operating on a server as well as web-hosting capacity.   
<!-- #endregion -->

Voyager was originally created for the curators, educators and exhibition designers at the Smithsonian to enrich and enhance the thousands of publicly available 3D models available from the Smithsonian’s website. The ability to provide multimodal annotation and apparatus within the same viewing environment as the 3D model itself stands in contrast to other museums which, by and large, display their 3D models through the Sketchfab API directly onto an institutional page accompanied by object metadata ([Figure 5](#anchor-figure-5-*)). While these models may be downloadable and provide a level of engagement for users beyond basic viewing of a 2D image (turning the model to see all sides of the object, zooming in, etc.), they, nevertheless, exist within a constrained informational rather than a narrative space. Voyager, on the other hand, provides a multimodal narrative environment, with a 3D model at its centre. As such, it provides an intermedial space from which to construct novel narrative paths.

```python tags=["figure-5-*", "anchor-figure-5-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 5: Left - Bacchante, Virtual Museums of Poland Project integration of Sketchfab API into online archive; Right - VélocipèAlienor, Council of Museums, France integration of Sketchfab API. "
            ]
        }
    }
}
display(Image("media/figure_5.jpg"), metadata=metadata)
```

## Beyond Representation: Intermedial Narratives

<!-- #region citation-manager={"citations": {"cite2c-8908013/HX5DKMUY": [{"id": "8908013/HX5DKMUY", "source": "cite2c"}], "cite2c-8908013/UQWM6FEY": [{"id": "8908013/UQWM6FEY", "source": "cite2c"}]}} -->
One way to think of the Voyager interface is as one that replicates traditional functions of museums, from museum tours to providing informational cards on individual objects,  to  audio tours, to longer narrative panes common in special exhibitions. Voyager story replicates these functions through tours, annotation, and articles, respectively. Through these functions curators can provide virtual visitors with information and anecdotes as they would in a physical setting.
As such, Voyager Story provides an intermedial experience of an object, scene, or space. Intermediality provides a framework to describe interrelationships between various media: e.g., the different communication and representational strategies when there is a crossing of borders between media, for example, when a novel is adapted into a film. For the purposes of this article, we employ the term in the creation of a narrative in which different media are combined, both explicitly and implicitly, to convey a scholarly argument and/or narrative. Or as <cite id="cite2c-8908013/UQWM6FEY"><a href="#cite2c%7C8908013%2FUQWM6FEY">Rajewsky (2005)</a></cite> writes, the creation of a ‘medial constellation’ in which each media element contributes to ‘the constitution and signification’ of the digital edition (p. 52). This signification includes decisions as to the forms and formats are optimal to advance the narrative (including audio, images [moving or still] or text), and where and how in the representational space afforded by Voyager Story should these multimodal elements be introduced.

Our conceiving of the narration in terms of intermediality has as its centre a new model of (re)presentation – what  <cite id="cite2c-8908013/HX5DKMUY"><a href="#cite2c%7C8908013%2FHX5DKMUY">Jens Schröter (2011)</a></cite> calls ‘transformational intermediality’ – to create a deep narrative and annotative structure in and around the 3D model. Transformational intermediality occurs when one medium (representing) refers to another (represented). This process allows for a transformation of the represented medium’s individual qualities, meanings and modes of expression. As a result, the represented medium is defamiliarised from its everyday, ‘normal’ state of being to encompass how the media hybridisation creates new aesthetic, narrative or communicative possibilities. As a result, the representing medium is able to comment on the represented medium in ways that influence or challenge how we perceive, access or examine the represented medium. In the case of 25 Northumberland Road as viewed within Voyager ([Figure 6: Left](#anchor-figure-6-*)), the 3D model of the building is the representing medium while the actual physical building located in Dublin is the represented medium ([Figure 6: Right](#anchor-figure-6-*)). As a result of the transformational intermediality occurring via Voyager, our experience of and approach to narrating about the building and its role during the Battle of Mount Street Bridge is different than if we were to give a live tour of the physical building.
<!-- #endregion -->

```python tags=["figure-6-*", "anchor-figure-6-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 6: Left - Screenshot of the 3D reconstructed model of 25 Northumberland Road as viewed in Voyager; Right - Screenshot of Google Maps view of 25 Northumberland Road (© Google 2023)."
            ]
        }
    }
}
display(Image("media/figure_6.jpg"), metadata=metadata)
```

We argue that the apparatus surrounding the model helps to mitigate the powerful illusory quality 3D models can have. Within the new intermedial narrative being created, the modelling of the scene of the battle becomes one modality through which meaning is created. As a result, the model is repositioned as a node in the meaning-making process through its relationships between people and things, at a specific time, place, and socio-historical context.


## 25 Northumberland Road as an Intermedial Narrative Through Voyager Story



### History of The Battle of Mount Street Bridge

<!-- #region citation-manager={"citations": {"cite2c-8908013/57PB9HMA": [{"id": "8908013/57PB9HMA", "source": "cite2c"}], "cite2c-8908013/9NNGAJCS": [{"id": "8908013/9NNGAJCS", "source": "cite2c"}]}} -->
The Battle of Mount Street Bridge was a significant encounter between Irish and British combatants that took place during the wider conflict known as the 1916 Easter Rising. The opening of the Rising began around midday on Monday 24 April 1916, approximately a year and a half into the First World War, when Patrick Pearse, read a proclamation of Irish independence from Great Britain on behalf of the ‘Provisional Government of the Irish Republic’ on the front steps of the General Post Office in Dublin’s Sackville Street (now O’Connell Street) (<cite id="cite2c-8908013/9NNGAJCS"><a href="#cite2c%7C8908013%2F9NNGAJCS">(Townshend 2006)</a></cite>).

In anticipation of British rebuttal, over 1,200 members of the Irish Volunteers, Irish Citizen Army, Hibernian Rifles and Cumin na mBan took up positions in buildings around Dublin, as well as the public park of St. Stephen’s Green. Meanwhile, the British responded by redirecting a brigade of four battalions of the Nottinghamshire and Derbyshire Regiments (known as the Sherwood Foresters) from their intended destination of France to Dublin to reinforce the British garrison stationed there. This brigade landed at Kingstown (today Dún Laoghaire) in the early hours of Wednesday, 26 April and moved on Dublin’s city centre in two columns ([Figure 7](#anchor-figure-7-*)). The left column, made up of the 2/5th and 2/6th Battalions arrived at the Royal Hospital at Kilmainham without major incident. However, the 2/7th and 2/8th Battalions (with c 1,750 soldiers) had as their destination Trinity College Dublin in the city centre (<cite id="cite2c-8908013/57PB9HMA"><a href="#cite2c%7C8908013%2F57PB9HMA">(Hughes et al. 2017)</a></cite>).
<!-- #endregion -->

```python tags=["figure-7-*", "anchor-figure-7-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 7: Map showing the two routes that the Sherwood Foresters took to enter Dublin’s city centre from Kingstown (Hughes, Campbell, and Schreibman 2017)."
            ]
        }
    }
}
display(Image("media/figure_7.jpg"), metadata=metadata)
```

<!-- #region citation-manager={"citations": {"cite2c-8908013/57PB9HMA": [{"id": "8908013/57PB9HMA", "source": "cite2c"}]}} -->
It was at one of the crossings on the Grand Canal at Mount Street Bridge, that they encountered fierce opposition by a small contingent of 17 Irish Volunteers spread across four buildings – 25 Northumberland Road, St. Stephen’s Parochial Hall, Clanwilliam House and Robert’s Builders Yard. It took the British an entire day to advance beyond Mount Street Bridge and suffered a total of approximately 160 casualties (<cite id="cite2c-8908013/57PB9HMA"><a href="#cite2c%7C8908013%2F57PB9HMA">(Hughes et al. 2017)</a></cite>). On the Irish side, four of 17 Volunteers were killed, including the unit’s Commanding Officer, Michael Malone. Malone and another Volunteer, Seamus Grace, were stationed in 25 Northumberland Road, the first building to be encountered by the British. These two men were able to hold off the British for several hours before the building was taken by heavier ammunition.

As a result of archival historical sources and interviews of witnesses and combatants in later decades, it is possible to construct a fairly accurate account of events, although discrepancies exist as some accounts were provided decades later, while others were limited by perspectival information available at the time. These sources include witness statements and other records from the Irish’s Bureau of Military History, Pension Records of Irish Volunteers as well as British Regimental Diaries of the Sherwood Foresters, extant pocket diaries, British Regimental Histories, and newspaper articles. Unfortunately, the official War Diaries of the 2/7th and 2/8th for 26 April are not extant for the dates of the Rising. While the Irish, in military terms, lost this battle, as well as the Rising itself, it is considered a symbolic victory as public opinion shifted from pro-British to pro-Irish sentiments after the executions of the uprising’s leaders (<cite id="cite2c-8908013/57PB9HMA"><a href="#cite2c%7C8908013%2F57PB9HMA">(Hughes et al. 2017)</a></cite>), leading, ultimately, to Irish independence in December 1921.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
### The Development of 25 Northumberland Road as an Intermedial Narrative
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
#### The 3D Model
<!-- #endregion -->

<!-- #region citation-manager={"citations": {"cite2c-8908013/JWJAWNDI": [{"id": "8908013/JWJAWNDI", "source": "cite2c"}], "cite2c-8908013/XMN4SKMM": [{"id": "8908013/XMN4SKMM", "source": "cite2c"}]}} tags=["hermeneutics"] -->
The 3D model of 25 Northumberland Road was extracted from a Unity project made in 2015 by NoHo (Dublin, Ireland) for the Contested Memories Project. The Unity version of the project contains the entire neighbourhood surrounding the area of the battle, including a 3D (re)construction of the residential housing, roads and environment. This (re)constructed scene is based on a variety of source data, including: a highly detailed point cloud data from a laser scan survey of Northumberland Road conducted by the Discovery Programme Centre for Archaeological Research and Innovation; Google Earth Imagery; the 1911 Ordnance Survey of Dublin; archival photographs taken after the Rising; and site visits. The modelled scene was created using 3DS Max together with textured coordinates for accurate lighting and physical appearance. The scene was exported from 3DS Max as an FBX file and imported into the Unity Engine as an Asset. The real-time interactivity in Unity allows online users to explore the 3D world at their leisure with free-roaming and user-directed cameras, instead of predefined paths, views and orientations (<cite id="cite2c-8908013/JWJAWNDI"><a href="#cite2c%7C8908013%2FJWJAWNDI">(Papadopoulos & Schriebman 2019)</a></cite>).

From this larger (re)constructed model in Unity, the single building of 25 Northumberland Road was selected in order to test out the suitability of Voyager for the PURE3D Infrastructure. Once the 3D model of 25 Northumberland Road was isolated, it was uploaded to Blender and exported as a GLB file. The 3D file requirements of Voyager are such that only models in a glTF or GLB file format can be ingested. The [GL Transmission Format (glTF)](https://www.khronos.org/gltf/) is an open source and royalty free 3D file standard that supports one or more 3D models, animations or moving scenes (<cite id="cite2c-8908013/XMN4SKMM"><a href="#cite2c%7C8908013%2FXMN4SKMM">(Khronos Group 2023)</a></cite>). Since 2017, glTF 2.0 was introduced whereby Physically Based Rendering (PBR) texture materials are incorporated into the file data. The difference between glTF and GLB is that for glTF, which is based on JSON (JavaScript Object Notation), some data (like textures, shaders or geometry and animation data) are stored externally in other file formats (JPEG, PNG, GLSL or BIN) whereas with GLB the file is based on binary data, which internally stores these other data types (<cite id="cite2c-8908013/XMN4SKMM"><a href="#cite2c%7C8908013%2FXMN4SKMM">(Khronos Group 2023)</a></cite>).
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
#### Setting up 25 Northumberland Road in Voyager
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Once the PURE3D Project set up the Voyager System on institutional servers, it was possible to input the GLB file of 25 Northumberland Road into a Voyager Story Scene using a secure back-end file management system called NextCloud. A file manager operating in the background is a necessary element of any Voyager Scene as the Voyager Toolkit is not a self-contained 3D viewer/editor as well as a file manager. The base files needed to visualise a 3D model in Voyager are only two: 1) the 3D model in a GLB/glTF file format (e.g., 25North_clean.glb) and; 2) the special Voyager-specific JSON.SVX file (e.g., scene.json.svx), an example of which is available on their documentation page in [Github](https://smithsonian.github.io/dpo-voyager/explorer/scene-create/).
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
These two files are stored within a single folder (e.g., 25North) in the file manager (in our case, NextCloud). The name of the project folder file path and the scene file name is then referenced in the URL link for accessing and editing the presentation in Voyager Story ([Figure 8](#anchor-figure-8-*)).
<!-- #endregion -->

```python tags=["figure-8-*", "hermeneutics", "anchor-figure-8-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 8: Breakdown of the URL link for creating a stable Voyager Story Instance."
            ]
        }
    }
}
display(Image("media/figure_8.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
The JSON.SVX file is the key element for each unique Voyager scene as it reads which 3D model to visualise as well as its scale and orientation, among other model settings. It is also the file that stores all the hotspot annotations and their settings in addition to the guided tour steps and commands which are created utilising the Voyager Story tool.

<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
#### Multimedia Resources
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The only elements not stored directly within the JSON.SVX file are the HTML articles and the multimedia files that are embedded within the articles. However, the JSON.SVX file references the HTML articles as they are created and stored in an ‘articles folder’. Within these HTML files, the multimedia resources (i.e. images, audio, video, or URL links or embedded content) are in turn referenced for visualising in the correct Voyager article.

As soon as a new Voyager Scene is created, the first automatic task of the toolkit is to create a folder called ‘articles’ within the Voyager Story Toolkit under the Media Tab in the scene file viewing window ([Figure 9: Left](#anchor-figure-9-*)). Simultaneously, in whichever file manager is operating in the background, that same folder called ‘articles’ is generated within the project folder alongside the GLB and JSON files ([Figure 9: Right](#anchor-figure-9-*)). When new articles are created in the Voyager Story Instance, they are automatically stored within this article folder. Additionally, when other multimedia files, such as JPEG, PNG, MP3, MP4, etc., are imported into the Voyager Instance, they are also stored within the ‘articles’ folder on the server.
<!-- #endregion -->

```python tags=["hermeneutics", "figure-9-*", "anchor-figure-9-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 9: Left - Location of the Articles Folder within Voyager Story; Right - Automatically generated Articles Folder located in NextCloud File Manager. "
            ]
        }
    }
}
display(Image("media/figure_9.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
The article editor in Voyager Story uses a WYSIWYG editor called [TinyMCE](https://www.tiny.cloud/) so that adding content to an HTML article occurs within a user-friendly interface that requires no knowledge of HTML coding. Besides the ability to create a title and body text with basic functionality to adjust place, text size and bold or italic, this editor also lets one insert images, video, audio, URL hyperlinks and embedded web-based content that is being referenced from another website or platform ([Figure 10](#anchor-figure-10-*)).

<!-- #endregion -->

```python tags=["hermeneutics", "figure-10-*", "anchor-figure-10-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 10: Screenshot of the TinyMCE WYSIWYG Voyager Story Article Editor."
            ]
        }
    }
}
display(Image("media/figure_10.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
For our implementation of 25 Northumberland Road, we wanted to use a diverse range of multimedia as a way to explore both the capabilities of the Voyager System as well as to understand the affordances of these different media types. Because the Contested Memories Project had already done extensive research on the battle, there were many archival sources to utilise. The  goal was to try to have at least one type of multimedia per article that would complement and enrich the text.

To that end, we included a number of images, such as portraits of the key players on both sides of the battle, as well as a map showing the route of the Sherwood Foresters from their landing place into the City Centre of Dublin. We also used an image of an excerpt from one of the witness statements from Seamus Grace, who was the only surviving Irish volunteer stationed at 25 Northumberland Road. For audio and video content, we embedded an audio clip from an RTÉ (Ireland’s National Public Service Media) radio special that recorded interviews of the surviving witnesses to the 1916 Irish Rising during a 50 year anniversary of the event. Another method of incorporating original statements made after the battle included a short video clip that contained a voice over of an actor reading another one of the witness statement excerpts from Seamus Grace with an animation of a typewriter taking down the account.

Additionally, we also had access to audio recordings of gunfire from the exact types of weapons used during the battle. We selected the gunshot recordings from the C96 Mauser hand pistol and the Long Lee Enfield Rifle which were the guns used by Malone and Grace when they were positioned in the building. These recordings were split between two articles, one on Grace’s weapon, the Lee Enfield, and the other on Malone’s weapon, the Mauser. Within these two articles we also embedded replica 3D models of the guns which were found on Sketchfab and embedded using the Sketchfab embed link.

The final type of multimedia we incorporated into the articles were URL links to original source material and relevant or interesting supplementary materials. With digital storytelling, hyperlinking can be a double-edged sword because you want to connect and reference your content to other interesting and detailed content found in the cornucopia of the web without losing your user to the hyperlinked website. Using the TinyMCE editor in Voyager, it is possible to have the setting that the hyperlink opens a new tab so that at least the user can come back to the Voyager Presentation after they have engaged with the external content.  

The only limitation we encountered to the TinyMCE Editor in Voyager is the ability to add captions to images as well as some margin space surrounding the image. Without this margin space, the text and image appear uncomfortably close together ([Figure 11: Left](#anchor-figure-11-*)). While these capabilities speak more to the aesthetics of the article layout, we found them to be an important aspect for visual readability. To circumvent this, we edited the HTML file directly and input the code for an HTML table caption that has a buffer of negative space surrounding it ([Figure 11: Right](#anchor-figure-11-*)). A comparison of these changes is in the figure below.
<!-- #endregion -->

```python tags=["hermeneutics", "figure-11-*", "anchor-figure-11-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 11: Left - Default margin space between text and image and no caption with the image; Right - Increased margin space between text and image after editing the HTML file and the addition of a caption for the image."
            ]
        }
    }
}
display(Image("media/figure_11.jpg"), metadata=metadata)
```

### Conceptualising the Narrative


The authors of this article developed the narrative around 25NR with three bachelors students (Sandra Martinez Böheme, Luca le Moine, and John Kausakis) enrolled in an Honours Course at Maastricht University’s Faculty of Arts and Social Sciences entitled “Making Scholarly Arguments in Three Dimensions”. The goal of the course was to provide students with the experience of developing a publicly-focused  3D edition through an intermedial narrative through the use of primary and secondary sources.

An early issue the project faced was a lack of examples for designing a space-based narrative utilising specific points on the 3D model to drive the narrative. We began by locating possible hotspot annotation by mapping known facts from the accounts of the battle to an image of the building ([Figure 12](#anchor-figure-12-*)). Based on this, the spatiality of the battle was analysed from a temporal perspective–what happened not only where but when (if known) and in what order. With these ideas mapped out, it was then decided that our implementation would include three guided tours:
- Tour 1: pre-battle events and preparations
- Tour 2: events  when the British troops arrived at the building;
- Tour 3: events that occurred in the aftermath of the battle (both in the short term as well as longer-term consequences)


```python tags=["figure-12-*", "anchor-figure-12-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 12: Google Jamboard of brainstorming session on information about the battle that could be physically identified."
            ]
        }
    }
}
display(Image("media/figure_12.jpg"), metadata=metadata)
```

Each student was responsible for authoring one tour. Google Slides were used to create  mock-ups of Voyager articles which would be incorporated within the tour. In order to avoid repetitiveness and make use of a wide range of multimodal sources, we created a media mapping by tour using a [Miro Board](https://miro.com/) ([Figure 13](#anchor-figure-13-*)).

```python tags=["figure-13-*", "anchor-figure-13-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 13: Miro Board mapping of the three tours and the various types of content and media included."
            ]
        }
    }
}
display(Image("media/figure_13.jpg"), metadata=metadata)
```

### Implementation in Voyager


Once all preparatory materials and mappings were complete, we came together to implement the content and configure the tours in Voyager.  The implementation is embedded below ([Figure 14](#anchor-figure-14-*)) and can be accessed via the [PURE3D Infrastructure](https://editions.pure3d.eu/project/1/edition/1/index.html). 

```python tags=["figure-14-*", "anchor-figure-14-*"]
from IPython.display import HTML, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "Figure 14: Voyager Explorer Implementation of 25 Northumberland Road",
          ]
        }
    }
}
display(HTML('<div class="sketchfab-embed-wrapper"> <iframe name="Smithsonian Voyager" src="https://author.pure3d.eu/viewer/0.46.1/read/64eca653b1520537c7ac5b06/update" width="800" height="450" allow="xr; xr-spatial-tracking; fullscreen"></iframe>'), metadata= metadata)


```

While we implemented using Voyager version 0.17.0, it has, since the time of publication, been updated and is currently at v.0.46.1. Therefore, there has been both minor and major changes to Voyager's functionality since we initially created the edition. This article describes our experiences and workflows at the time of implementation using the 17th version of the application. 

In the process of inputting content and making configurations, we discovered a number of visual and conceptual challenges that we had not anticipated. For example, the large number of hotspot annotations crowded the 3D object and sometimes prevented visibility of other annotations ([Figure 15: Left](#anchor-figure-15-*)). To counter this, annotations were subdivided into three groups using the Tag feature in Voyager. We also colour-coded the different groups to help with visual differentiation ([Figure 15: Right](#anchor-figure-15-*)).

```python tags=["figure-15-*", "anchor-figure-15-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 15: Left - Annotation label overcrowding; Right - Use of annotation tags to subdivide annotations into groups."
            ]
        }
    }
}
display(Image("media/figure_15.jpg"), metadata=metadata)
```

Another issue encountered was the conceptual disconnect between much of the article content, which frequently focussed on background information (such as information on the combatants, prior battle preparations, etc.) with the spatiality of the building. In other words, it was not possible to provide a camera view or movement to illustrate the article content. To overcome the text driving the edition, and so that there would be more interaction within the 3D space, a map was placed underneath the building as a means of providing a better understanding of the location of the building in regard to the other buildings and points of interest in the conflict. It also helped to illustrate the events of the battle occurring in the immediate vicinity of the building, such as the cross-roads where the British first arrived and engaged in gunfire with the Irish volunteers, or the path that Grace took in his escape from the rear of 25NR. We initially had these locations in maps embedded within articles, but by shifting this content to the 3D space, the overall understanding of the spatio-temporal aspects of the battle were improved.

Utilising a range of camera views and movements were key to taking advantage of the dimensionality of the 3D space, particularly in creating a sense of presence. For example, we provided camera views which allowed readers to ‘see’ the viewpoints that Malone and Grace would have seen from the window positions from which they were shooting ([Figure 16](#anchor-figure-16-*)).


```python tags=["figure-16-*", "anchor-figure-16-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 16: Left - First person perspective from the third floor bathroom window where Michael Malone was positioned (Tour 2, Step 10); Right - Inside the second story street-facing room where Seamus Grace was positioned (Tour 2, Step 13)."
            ]
        }
    }
}
display(Image("media/figure_16.jpg"), metadata=metadata)
```

<!-- #region citation-manager={"citations": {"cite2c-8908013/99U987DD": [], "cite2c-8908013/PPG6BQCB": []}} -->
This provided an opportunity for readers to come to their own conclusions about the affordances and drawbacks of the strategic position of the building which was the first position of Irish resistance encountered by the British on their march into the city centre. It is believed by scholars that although only two Irish soldiers occupied this building, the element of surprise combined with the corner vantage point (which allowed Grace and Malone to shoot both from Northumberland and Haddington Roads) was key to how they were able to hold off several British companies for several hours (<cite id="cite2c-8908013/PPG6BQCB"><a href="#cite2c%7C8908013%2FPPG6BQCB">(Coogan 2016)</a></cite>, <cite id="cite2c-8908013/99U987DD"><a href="#cite2c%7C8908013%2F99U987DD">(McGarry 2016)</a></cite>).

<!-- #endregion -->

## Reception (survey and focus groups)


The final stage of the project was to get feedback from individuals not associated with the creation of the edition. This took form in two modalities, an online survey using the Qualtrics software to get wider and general feedback on the 3D edition implementation of 25NR and an in-person focus group for a more nuanced discussion with a specific demographic group of non-academic individuals interested in the historical content of the edition. Seeking feedback had two objectives: 1) to gather initial impressions of the implementation in terms of navigation and usability of Voyager, especially for further usage in the PURE3D infrastructure; and 2) to understand if our implementation of 25NR was successful in terms of narrative techniques and methods. The feedback was key for improving, not only 25NR, but also for informing strategies for planning subsequent editions on the other buildings involved in the battle.


### The Survey


The survey contained 56 questions and was divided into four sections:
1. Demographics: age, gender, occupation as well as questions on their interest in history, and their familiarity with the historical content and technology in general;
2.  Navigation: questions pertinent to user interface and user experience;
3. Presentation: questions about the structure of the narrative and multimedia content;
4. Historical content: which asked participants to reflect on both the breadth and depth of the historical information presented, as well as a series of quiz-type questions that allowed us to see if and how much of the content was retained by the participants.


<!-- #region tags=["hermeneutics"] -->
#### Survey Analysis
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The survey was sent to a small sample of people associated with the Contested Memories Project and PURE3D (including the focus group participants). This occurred in two phases with a total collection of 29 responses. In the first phase, the survey was circulated to The Irish branch of the Western Front Association, to family and friends of the Honours students who participated in the project and PURE3D’s pilot partners. About a year later, the survey was circulated in a second phase to workshop participants at the 2023 Conference of Computer Applications in Archaeology which was hosted that year in Amsterdam.

With the exception of a few multiple choice questions and spaces for participants to add their own short-text responses, the majority of survey questions were based on a 5-point Likert scale to assess their general attitude towards the Voyager presentation of 25NR. The following sections summarise a small selection of the 56 questions posed in order to demonstrate the overall sentiments that respondents had towards the edition.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
##### Demographics
<!-- #endregion -->

```python tags=["hermeneutics", "figure-17-*", "anchor-figure-17-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 17: Age and Gender distribution of the survey participants. Left: 29/29 responses; Right: 29/29 responses."
            ]
        }
    }
}
display(Image("media/figure_17.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
Demographic questions asked of the respondents included age, gender and occupation. In terms of age, the range of ages was from 18 to 74 years old with the largest number of respondents coming from the 18-34 age group (45%) while both the 35-54 age group and the 55-74 age group each represented 27.5% of the total ([Figure 17](#anchor-figure-17-*)). Gender distribution was divided almost evenly with 52% who identified as female and 45% as male, one respondent identified as non-binary or third gender ([Figure 17](#anchor-figure-17-*)). In terms of occupation, the largest portion of the respondents (48%) stated higher education or academia as their profession, responses ranged from ‘student’ to ‘professor’. Because of the focus group target audience, some respondents (17%) stated that they were ‘retired’. The remaining respondents who answered the question (24%) can be identified under cultural heritage professions, including educators, digitization specialists or archaeologists. 11% of respondents chose not to respond to this question.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
##### Navigation
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The Navigation section of the survey focused on gathering feedback regarding the respondents’ experience with Voyager. A selection of questions from the Navigation section which illustrate general sentiments are presented below.

Regarding the respondents’ overall reception of the interface, a multiple choice question was posed offering adjectives to describe their experience. Top responses were for the positive adjectives of ‘engaging’ (59%), ‘intuitive’ (34%) or ‘flexible’ (24%). Some respondents felt it was ‘repetitive’ (28%), ‘overwhelming’ (17%), ‘simplistic’ (10%) or ‘confusing’ (10%).

In terms of how difficult the respondents found receiving information via the interface, 44% of those who responded found it to be ‘not at all’ challenging, 37% said it was ‘slightly’ challenging. However, 11% felt it was ‘moderately challenging’ and 7% stated that it ‘very challenging’ ([Figure 18](#anchor-figure-18-*)). For the clarity of the icons used in the navigation, 22% of respondents felt that they were ‘extremely clear’, 41% felt they were ‘somewhat clear’. However, 11% stated that the icons were ‘neither clear nor unclear’ and 26% felt they were ‘somewhat unclear’. None of the respondents indicated that the icons were ‘extremely unclear’.  

A few questions were posed as to the suitability of the interface for structuring content so that it was organised and understandable. Tours were found to be ‘extremely helpful’ in structuring content for 40% of respondents, ‘very helpful’ for 44% and ‘moderately helpful for 16%. No respondent felt that the tours were only ‘slightly’ or ‘not at all helpful’. Regarding the overall technology of Voyager for understanding the battle ([Figure 18](#anchor-figure-18-*)), 20% found it to be ‘extremely’ useful, 60% said it was ‘very useful’, 16% indicated it was ‘moderately useful’ and 4% said it was only ‘slightly’ useful. However, no respondents felt that the Voyager technology was ‘not useful at all’.  

<!-- #endregion -->

```python tags=["hermeneutics", "figure-18-*", "anchor-figure-18-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 18: Sample of questions from the Navigation Section of the survey. Left: 27/29 responses; Right: 25/29 responses."
            ]
        }
    }
}
display(Image("media/figure_18.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
##### Presentation
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The Presentation section of the survey posed questions that related to our specific use of the Voyager system to create a 3D storytelling experience that focused on the use of a 3D asset and multimedia resources to guide viewers through the events that took place at 25NR during the Easter Rising. A selection of questions from the Presentation section which illustrate general sentiments are presented below.

Regarding the presence of the 3D model within the presentation ([Figure 19](#anchor-figure-19-*)), 60% felt that it ‘definitely’ added value to their understanding of the content, 36% indicated that it ‘probably’ did and 4% said it ‘probably did not’. No respondent felt that it ‘definitely did not’ add value to their understanding. Another similar question asked them to describe their understanding of the event after interacting with the 3D model and accompanying information in this presentation. Of those who responded to this question, 36% would describe their understanding as ‘extremely good’, 44% said their understanding was ‘somewhat good’ and 20% felt that their understanding was ‘neither good nor bad’. No respondent indicated that their understanding of the events was ‘extremely’ or ‘somewhat bad’.

When asked a multiple choice question regarding the addition of multimedia embedded into the articles with short text-based descriptions ([Figure 19](#anchor-figure-19-*)) very few responded with adjectives that would describe this as either ‘superfluous’ (3%) or ‘distracting’ (3%). The remaining responses focused on positive adjectives of ‘enriching’ (59%), ‘useful’ (45%), ‘complementary’ (38%), and ‘engaging’ (31%).

One question was posed to understand how the respondents felt about the style of the presentation, if it was more of a journey on which they were taken via a narrative or if it felt like it was more like receiving information from a newspaper article. For a ‘story-like’ presentation, 28% of respondents felt this was ‘extremely story-like’ and 32% felt it was ‘somewhat story-like’. As for a more ‘article-like’ presentation, 4% of respondents felt it was more ‘article-like’ and the remaining 36% felt that it was ‘a bit of both’ styles. No respondents indicated that it was neither of these styles.

Finally, when asked if they would be interested in exploring more aspects of the battle using a similar presentation within Voyager, 52% indicated that they ‘definitely would be’, 40% said they ‘probably would be’, and 8% said they ‘may or may not’ be interested. No participant responded that they ‘definitely’ or ‘probably would not’ be interested in exploring more aspects of the battle this way.

<!-- #endregion -->

```python tags=["hermeneutics", "figure-19-*", "anchor-figure-19-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 19: Sample of questions from the Presentation Section of the survey. Left: 25/29 responses; Right: 25/29 responses."
            ]
        }
    }
}
display(Image("media/figure_19.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
##### Historical Content
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The Historical Content section contained questions designed to understand how users responded to the text-based content of the presentation. Our intention was to write clear, concise and relevant material that would outline the contours and nuances of the battle and its  combatants. A selection of questions from the Historical Content section which illustrate general sentiments are presented below.

One question sought to understand how respondents felt about the amount of text offered in the presentation. While 6% of those who responded felt it was ‘far too much’ text, 23% said it was ‘slightly too much’ and the remaining 71% felt it was ‘neither too much nor too little’. None expressed an opinion that there wasn’t enough text-based content.

Another question asked the respondents to describe their level of engagement with the historical content presented ([Figure 20](#anchor-figure-20-*)). Of those who responded to this question, 12% found the historical content to be ‘extremely interesting’, 76% described it as ‘very interesting’ and 12% found it ‘moderately interesting’. No respondents felt that the content was ‘slightly interesting’ or ‘not interesting at all’.

One of the questions was designed to understand if the respondents felt the narrative of events was clear ([Figure 20](#anchor-figure-20-*)). Of those who responded to this question, 6% found it to be ‘extremely unclear’, another 6% said it was ‘somewhat unclear’, while an additional 6% felt it was ‘neither clear nor unclear’. On the other hand, 35% of the participants found it to be ‘somewhat clear’, and 47% stated that the narrative was ‘extremely clear’.
<!-- #endregion -->

```python tags=["hermeneutics", "figure-20-*", "anchor-figure-20-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 20: Sample of questions from the Historical Content Section of the survey. Left: 17/29 responses; Right: 17/29 responses."
            ]
        }
    }
}
display(Image("media/figure_20.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
#### The Focus Group
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Since the audience for the edition was envisioned to be a public audience, it was decided to conduct a focus group with individuals who would have an interest in the period, but who were not experts. These participants, who were familiar with the Irish history of the period, but not the battle itself, engaged with the Voyager Explorer of 25NR through the survey in advance of the focus group session. An in-person focus group was held in Dublin in June 2022 with six individuals. Five were members of the Irish Great War Society (a non-academic society for individuals interested in the First World War), while the sixth was a secondary school educator who had several years earlier participated in a related 1916 project, Letters 1916. The majority of the six participants for this focus group were from an older age group and most were retired. Advertisement for the focus group was limited to a special interest group in First World War history. Therefore, this particular group was already interested in early 20th century history, although not necessarily with the details of the battle. Although complementary, this differed greatly from the general feedback from surveys circulated to heritage scholars more interested in the technological applications rather than the historical context of the famous battle. As a result, the focus group provided our team with an opportunity to engage with a small group of non-expert members of the public who could provide critical, content-based feedback about the interweaving of historical narrative within a 3D viewing environment.

The focus group was conducted with a series of interactive activities from the [Design Methods Toolkit](https://toolkits.dss.cloud/design/) which allowed participants to express their thoughts in an open and creative way: a Plus/Delta exercise that captured aspects of Voyager Explorer and its content that participants liked and the aspects that they would like to see improved; and a Love/Break-up letter addressed to the experience of learning about history using Voyager as the mediator of the narrative. These were followed by a discussion.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
##### Plus/Delta Analysis
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
For the Plus/Delta exercise, as a first step, participants used post-it notes to write single words or short statements about the 25NR that they appreciated and placed these under the ‘Plus’ side of a large board, and for aspects that they felt needed improvement they placed the post-it notes on the ‘Delta’ side of the board ([Figure 21](#anchor-figure-21-*)). The second step involved grouping the similar post-it notes into groups. The following sections summarise the results of this exercise.
<!-- #endregion -->

```python tags=["hermeneutics", "figure-21-*", "anchor-figure-21-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 21: Results from the Plus/Delta Exercise with Focus Group Participants in Dublin, Ireland."
            ]
        }
    }
}
display(Image("media/figure_21.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
*Plus:*

In terms of positive aspects of the Voyager presentation, we can observe from the responses that the participants felt the ‘storytelling’ quality was a commonly appreciated feature, both in the style of presentation as well as the personal stories about the combatants. Another clearly favoured aspect was the scholarly features of the presentation, namely the neutral tone which didn’t pick a side of the conflict to garner sympathy, along with a clear bibliography of sources used. Finally, the participants appreciated the multimedia resources, particularly the 3D model, the hyperlinks to external sources, and the multisensory aspects of the narrative.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
*Delta:*

For aspects of the Voyager presentation of 25NR that could be improved, the participants identified a number of points for future consideration. For one, there seemed to be technical malfunctions for the audio clips that were embedded in a few of the articles. The participants also felt that the inclusion of the gunshot recordings was not necessary and it was recommended to make it clear what purpose the gunshot serves in the narrative.

Another area that they felt had room for improvement was the onboarding of how to use and interact with Voyager. They suggested a printable instruction sheet or video at the beginning to get started. They also requested that there be more visual materials and that some of the materials (i.e., the embedded map) should be larger so that they can be more closely examined. They also felt that there could have been more interactivity or that the realism for viewing perspectives from the windows could be improved. Final comments included more information and details on the British movements and their decision-making process as well as more personal stories of ordinary-rank British combatants.

<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
##### Love/Break-up Letter Analysis
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
The Love/Break-up Letter exercise is also an activity from the [Design Methods Toolkit](https://toolkits.dss.cloud/design/method-card/break-uplove-letter/). It acts similarly to the Plus/Delta exercise in that it asks participants to think about aspects of a product that they appreciate and which aspects were not as satisfactory. However, this individual  exercise asks  participants to evaluate the product in terms of an emotional and personal response. Participants can either express their love for the product or criticise where the product has failed to impress or keep their affection, resulting in a desired termination of the relationship. It is also possible to write a more nuanced letter which is not a clear love or break up letter. A digital copy of each letter can be viewed below ([Figure 22](#anchor-figure-22-*)) and a short summary of the responses is presented in the following section.
<!-- #endregion -->

```python tags=["hermeneutics", "figure-22-*", "anchor-figure-22-*"]
from IPython.display import Image
metadata={
    "jdh": {
        "module": "object",
        "object": {
            "type":"image",
            "source": [
                "Figure 22: Love/Break-Up Letters written by Focus Group Participants in Dublin, Ireland."
            ]
        }
    }
}
display(Image("media/figure_22.jpg"), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
The overall sentiment appeared to indicate that Voyager needed some self-improvement. FGP 3 stated it well when they wrote: “In summary, you’re a wonderful participant in my life, but I don’t see a long term relationship in our future unless you grow and improve a little”. Similarly, FGP 2 wrote “this is a good beginning in our relationship, but we need to do more to have an output to endure and realise our potential”. Finally, FGP 1 expressed similar feelings regarding a desire that Voyager make some changes in order for their relationship to last longer:

>The relationship has deepened my emotional experience of what was happening around us yet at the same time I am pragmatic… I cannot see myself establishing a long term relationship [and] to contemplate a lifelong commitment would be beyond reflection.

While these excerpts clearly indicate that there is a break-up occurring, it  also implied that this is not an outright termination. Instead the participants demonstrate their willingness to continue a relationship, as long as improvements are made.

As with the Plus/Delta exercises, there were some recurring sentiments expressed by the participants. For example, more than one letter mentioned their distaste for the audio recordings of the shots from the guns used by the Irish Volunteers. As one participant wrote, “I didn’t see the point of this” (FGP 3) and another said they were “very irritating”. On the other hand, the audio recordings and oral accounts by individuals present during the battle were greatly appreciated. FGP 2 stated in their letter that the “oral presentations contained in Voyager were what [they] enjoyed the most” and FGP 3 mentioned that alongside the animations, the “auditory accessories helped to retain information”.

Another issue brought up in the Plus/Delta exercise that was elaborated on in the letters was the difficulty in getting started with the technology. FGP 4 wrote about their experience with digital literacy: “I couldn’t understand you. As if we were speaking different languages, all the signs were familiar, even the words but I just couldn’t make sense of them”. However, this same participant explained that once this issue of translation was resolved they “just fell in love [with it] after that. [It] became so accessible then, so inviting, so charming with lots of wonderful secrets [it was] more than willing to share.” (FGP 4). Similarly, FGP 2 indicated that although the software was “easy to use and manipulate…it would be preferable to have a printed sheet with the instructions for use”.

A final critique expressed in more than one letter was that there could have been more development of the 3D scene and interactivity within it. FGP 2 felt that the building, while “impressive”, could have been complemented with more of the “surroundings and the movement of the Sherwood Foresters”. FGP 3 had a similar reaction of appreciation of the 3D presentation and vantage points but desired to “see more, experience more”. To illustrate this request, they wrote: “I would have liked to feel I was actually standing there. What would I see below me? An empty street? Some worn shattered windows? An advancing army?”

<!-- #endregion -->

## Discussion


Our experience of conceptualising and implementing a 3D narrative in Voyager, coupled with the results of the feedback, provided us with four main insights to create intermedial 3D edition-based narratives.



##### The Semantic Language of a 3D Interface


There is not a consistent semantic language associated with 3D interfaces. For those typically developed in Unity, the ability to create a user experience and bespoke interface to support that experience is a strength of the system. Other 3D viewers (see [Choosing Software for the Infrastructure](#anchor-1-1-1) for a review some of these) do not share a semantic language of icons, the spatial arrangement of model to text to multimedia, animations (e.g., camera angles and viewpoints), and first vs third person navigation, which would make it easier for users to engage with multiple interfaces and take full advantage of the affordances of the systems.  

While analysis of the feedback revealed a generally positive response to navigation within Voyager, the lack of an intuitive understanding of the interface’s semantics, impeded users' engagement. There was no onboarding guide to the user interface, and while there are tool tips when one hovers over an icon, it was not necessarily clear what, for example, an ‘interactive tour’ entailed, or why one would want to ‘read articles’ if they  were engaging with 3D. Hence several users did not take advantage of all the navigational throughways facilitated by the interface (e.g., tours, navigating from one article to the next,  or navigating to articles via hotspot annotation). This lack of clarity made their journey through the interface haphazard and somewhat random. Those that missed the tour feature missed out on camera viewpoints that supported the narration. Thus the semantics of system features need to be more intuitive, coupled with clear help and tool tips.


##### Personal Stories within 3D Narratives

<!-- #region citation-manager={"citations": {"cite2c-8908013/IHFRW2QK": [{"id": "8908013/IHFRW2QK", "source": "cite2c"}]}} -->
Feedback from the survey and focus group revealed that users appreciated the many personal stories of those involved in the conflict. Some participants noted that as they navigated the edition, this generated an evocative and emotional response. As editors, we chose both Irish and British accounts as a means of re-framing the narrative instead of favouring one perspective over another. There was an abundance of personal information on the two Irish combatants involved in the battle. The personal story highlighted on the British side is a well-documented story of  [Frederick Christian Dietrichsen](https://mountstreet1916.ie/battle-of-mount-st/british-officers/#Dietrichsen) (1882-1916), 2/7 Sherwood Foresters and adjutant, C company. Dietrichsen was killed by fire from No. 25 Northumberland Road and was among the first casualties of the battle just hours after greeting his Irish-born wife and child who were staying with her family and turned out to greet the British troops on their march into the city centre. Nevertheless, participants requested that at least one additional story of an enlisted British soldier also be included to reflect more contemporary concerns of history by highlighting the experiences of ordinary people (<cite id="cite2c-8908013/IHFRW2QK"><a href="#cite2c%7C8908013%2FIHFRW2QK">(Lyons, 2010)</a></cite>).
<!-- #endregion -->

#####  Object-Centred Narratives


The majority of those who took the survey found the framing of the edition around a  3D model not only added value to their understanding of the historical event, but created an engaging learning experience. This approach, however, can be challenging as not every object lends itself to this treatment. For example, interest in a particular object may not be vested in its surface features, but in its historical importance. In this case, the intermedial interweaving between annotative information and multimedia that is reflected on or through the 3D model may not be easily accommodated: e.g.,  the model itself may not have the semantic richness necessary to communicate its own story. On the other hand, it may also be that we are not yet practised in developing object-centred narratives and that different design processes are necessary to draw out the latent narratives embedded in the ‘physicality’ of the object.

Within the user feedback, there was a repeated desire to see and experience more of the spatial physicality of the battlefield by including more in the 3D scene of the buildings and street environment surrounding 25NR. This point is especially salient as much of the first person accounts cite buildings, streets and areas that go beyond the single building focused on in this edition. We anticipated some of this criticism and tried to ameliorate it by incorporating a map (see figures 14 a and 14b) to locate the building in cartesian space and via combatant viewpoints – both from the outside of the building as well as from within the building (such as window viewpoints) onto the street. However, this technique fell short as the view points looked into a black and empty space, as noted by the focus group and survey participants. In a future iteration we will add back into the 3D space more of the battlefield from the original Unity build.


##### Assembling a 3D Medial Constellation


Study participants felt the inclusion of a diversity of multimedia enhanced their learning, embodying Rajewsky’s concept of medial constellation. Especially valued were the short clips of witness accounts, either featuring original voices or read by a member of the project team taken from written first person accounts. Participants requested that more first person narratives be included (providing more bottom up accounts of the battle) while also requesting that audio recording of the articles be made available alongside the written text-based articles. This request is perhaps unsurprising in that additional aural sources enhance multisensory simultaneity.

Nevertheless, annotating in multiple media can also lead to content being repetitive between media types (as opposed to additive) and/or a disjointed and/or confusing presentation. This is especially true with object-centred narrative which may not necessarily have a strong narrative focus. Feedback from the study group indicated that our implementation of the media constellation was overall effective in that, by and large, each medial element complemented and contributed to the overall narrative. One of the few exceptions was the embedding of gunshot recordings of period guns. As there was no signposting as to the content of the audio, thus when participants played the clip they found the recording unexpected, jarring, and gratuitous.  While the intention of including the clip was to enhance the multisensory constellation, given its content, and its lack of signposting (including a trigger warning), its inclusion had the opposite effect. These recordings have since been removed. In order for them to be reincluded, clearer signposting would need to be made between the media and the narrative.


## Conclusion


Despite the fact that the feedback gathered was relatively modest in size, it was fairly consistent. The 3D implementation itself was generally well-received in terms of the historical content and the enriching multi-media used to complement the text-based narrative. However, sparsity of the 3D scene as well as technical issues with the Voyager software was frequently noted as hindering the overall experience.

It was clear from the feedback, from both academic and non-academic users, that the case study achieved its goal of creating a more engaging, immersive multi-modal experience of the battle while highlighting personal stories through a wide variety of primary and secondary sources. For the feedback that focused on usability, the results fed into subsequent discussions with the developers at the Smithsonian Institution to improve the software. This open communication and continued technical support for the system, together with the feedback gathered on Voyager, has led to our confidence in adopting Voyager as a suitable framework for developing 3D scholarly editions. For the feedback that focused on implementation, training material and workshops developed for the PURE3D Project embedded three key insights: 1) the 3D model needs to be at the centre of the narrative, materially and spatially; 2) in cases when the primary 3D model not semantically rich enough to be the centre of the story, other 3D models should be integrated into the scene to augment the narrative; 3) multimodal annotation should be additive rather than repetitive between media, with each node providing a piece of the narrative puzzle; 4) although an ordering is established in terms of tours and articles, users may choose to engage with the edition through a different order, much like a hypertext narrative, and the narrative arc must accommodate different entry points into the edition.

The opportunities for object-based 3D narratives, augmented by and through rich medial and annotative constellations, are in their infancy. While a platform like Voyager utilises a language not unfamiliar to museum narrative or informational structures (tours, object-information cards, and longer prose-based introductions to collections or subcollections), repositioning these within an electronic environment in which the 3D narrative is the central text, can be defamiliarising. This is, in part, because users do not necessarily recognise the physical equivalencies due to an unfamiliar set of signs within a novel and complex information space. However, even when users become comfortable with the environment, the appropriateness of the narrative to the medium, e.g., creating object-centred narratives, is key. The 3D model needs to remain the central text, augmented by multimodal content to create a rich multisensory experience, for users to engage with, to learn from, and to enjoy.


## Acknowledgements


This research was made possible through the PURE3D Project at  Maastricht University which is generously funded by the Platform Digitale Infrastructuur - Social Science and Humanities (PDI-SSH). PURE3D has received approval from the Maastricht University Ethical Review Board (ERCIC_294_29_09_2021) to conduct participant-based research. We would also like to recognise and express our gratitude to the Faculty of Social Sciences and Arts 2022 Honours students Sandra Martinez Böhme, Luca Moine and John Kaulakis at Maastricht University for their professionalism and dedication in developing the 3D Scholarly Edition for 25 Northumberland Road.
