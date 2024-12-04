# BevSG
Code and datasets for paper “Learning Bird’s Eye View Scene Graph and Knowledge-Inspired Policy for Embodied Visual Navigation”

## Learning Bird’s Eye View Scene Graph and Knowledge-Inspired Policy for Embodied Visual Navigation
We propose BevNav framework to solve these issues by three parts: (i) we introduce a novel Bird’s Eye View  
(BEV) scene graph (BevSG) that utilizes multi-view 2D information transformed into 3D under the  
supervision of 3D detection to encode scene layouts and geometric clues. It can distinguish multi-view  
semantically similar objects and make plans in this graph. (ii) we propose BEV-BLIP contrastive  
learning that aligns the BEV and language grounding inputs transferring constrain commonsense  
knowledge in pre-trained models without other training in the environments. (iii) we design BEV-  
based view search navigation policy, which encourages representations that encode the semantics,  
relationships, and positional information of objects. This policy leverages the topological relations of  
locally collected BEV representations to infer invisible objects.  
#
