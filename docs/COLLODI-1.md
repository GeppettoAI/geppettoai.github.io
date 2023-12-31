<h2>Abstract</h2>
<p>We present COLLODI, a conditional generative pipeline for 3D assets. Unlike recent work on 3D generative models which produce a non-textured meshes, and have long generation times. COLLODI builds upon multiple state of the art methods order to generate fully textured meshes in a matter of 2 minutes on a single A100 GPU.</p>
<h2>Video</h2>
{% include youtube.html id=Y5I8LIcDpRA %}

<h2>Background</h2>
<p>While there has been some novel advancements in text-to-3D in specific areas.  There has yet to be a fully end-to-end pipeline / model for creating fully textured 3D meshes in a reasonable amount of time.  COLLODI aims to push the needle of generativeAI for 3D forwards significantly.</p>
<h2>Method</h2>
<p>By combining multiple state of the art methods into a single pipeline we demonstrate that COLLODI is capable of generating guidable 3D meshes from only text.  Current methods rely or focus on one area of 3D creation while COLLODI represents an end-to-end pipeline for 3D mesh generation that includes text or image + texturing resulting in high-fidelity objects.</p>
<h3>Zero-Shot (Mesh creation)</h3>
<p>Unlike recent work on 3D generative models which produce a single output representation, COLLODI directly generates the parameters of implicit functions that can be rendered as both textured meshes and neural radiance fields. We train COLLODI in two stages: first, we train an encoder that deterministically maps 3D assets into the parameters of an implicit function; second, we train a conditional diffusion model on outputs of the encoder. When trained on a large dataset of paired 3D and text data, our resulting models are capable of generating complex and diverse 3D assets in a matter of seconds.</p>
<h3>One-Shot (Mesh creation)</h3>
<p>Given a single image, we first use a view-conditioned 2D
diffusion model, to generate multi-view images for the input view, and
then aim to lift them up to 3D space. Since traditional reconstruction methods
struggle with inconsistent multi-view predictions, we build our 3D reconstruction
module upon an SDF-based generalizable neural surface reconstruction method
and propose several critical training strategies to enable the reconstruction of 360-
degree meshes. Without costly optimizations, our method reconstructs 3D shapes
in significantly less time than existing methods. Moreover, our method favors
better geometry, generates more 3D consistent results, and adheres closely to
the input image.</p>
<h3>Texturing</h3>
<p>Leveraging a pretrained depth-to-image diffusion model, COLLODI applies an iterative scheme that paints a 3D model from different viewpoints. Yet, while depth-to-image models can create plausible textures from a single viewpoint, the stochastic nature of the generation process can cause many inconsistencies when texturing an entire 3D object. To tackle these problems, we dynamically define a trimap partitioning of the rendered image into three progression states, and present a novel elaborated diffusion sampling process that uses this trimap representation to generate seamless textures from different views. We then show that one can transfer the generated texture maps to new 3D geometries without requiring explicit surface-to-surface mapping, as well as extract semantic textures from a set of images without requiring any explicit reconstruction. Finally, we show that TEXTure can be used to not only generate new textures but also edit and refine existing textures using either a text prompt or user-provided scribbles. We demonstrate that our TEXTuring method excels at generating, transferring, and editing textures through extensive evaluation, and further close the gap between 2D image generation and 3D texturing.</p>
<h3>Anything-To-3D</h3>
<p>By creatively combining multiple state-of-the-art methods, we can achieve multi-modal generation of fully textured meshes in times that are feasible for not just general usage, but also usable in runtime applications and simulations.</p>
<h3>Examples</h3>
