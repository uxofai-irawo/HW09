# HW09

The two proposals that I am wanting to explore for this experimentation are ***Dorsal*** as a solution for addressing online privacy and safety, and ***Little Free Archives*** as a solution for creating community stewarded archives for marginalized histories. In reading some of the feedback I received, I feel confident in my exploration of Dorsal moving forward but there is still something about community memories of the Little Free Archives that interests me. In this experimentation, I am interested in asking *what purpose can AI serve for communal memory, history, and identity?* While I am apprehensive about whether AI can aid in preserving marginalized histories, I am curious about this tool as a question-inviting provocation, rather than a UX solution.

For Dorsal, the AI technologies that I imagine needing would be facial recognition and generative fill, these would likely require two separate models for first identifying whether it is a particular users face in a photo and then replacing the face with a new image generation. To explore these two steps independently first, I chose teachable machine to create a custom model and the stable diffusion model shared with us in class for generative fill to experiment with.

For the Little Free Archives, I would like to explore something similar to the work of [Brad MacDonald](https://www.bradmack.com/chatbots) taking ChatGTP and augmenting its voice based on the voice of a specific corpora. Therefore, the model I will be experimenting with is OpenAI.

## Facial Recognition
To start in exploring Facial Recognition, I looked at teachable machine and ml5.js just to see if I could train a model on images of my face to see if the model could verify that I am in fact me! To start I went into my Google Photos to export all of the photos that have my face in it (ended up being 79 photos). Then I went to Kaggle and grabbed a set of images of celebrities faces to train my model against

<img width="1440" alt="image" src="https://github.com/user-attachments/assets/9defc6b3-a490-4239-bff8-7376208f22ae" /> <br/>
<img width="1440" alt="image" src="https://github.com/user-attachments/assets/3976045f-3639-4425-8791-125273bc5257" /> <br />

As you may see in my testing, this attempt was not effective in rearing an accurate facial recognition program. I assume it might be because of the low amount of images of me represented compared to the images of celebrities? <br/>

As another more sucessful exploration, I looked at how I might be able to use teachabla machine with ml5.js to detect whether I was looking at the front or back of my face. Below is the model that I trained.

<br/>
<img width="1440" alt="image" src="https://github.com/user-attachments/assets/a5426a4c-738a-47b7-9a0e-80b9b175304c" />
<br/>

I then put the model in the following p5.js sketch to check the efficacy (https://editor.p5js.org/irawoajasin/sketches/TynsevOXT). I tested this on my camera feed as well as showing the model other photos of me either facing or not facing the camera. It was actually quite accurate for more recent pictures of me but not as accurate for photos of older photos or photos of other people. That said, if this is only for a particular user, maybe it is ok for the model to only be trained on you (i.e. go through an onboarding where a ml model gets trained on your face and photos of you). Below are some of the tests I did:

<br/>
<img width="662" alt="image" src="https://github.com/user-attachments/assets/387b5a94-35fd-4272-b10a-e0cc6c5d1a80" />
<img width="669" alt="image" src="https://github.com/user-attachments/assets/cea7136f-431c-43c1-81ca-b864cacc5792" />
<img width="653" alt="image" src="https://github.com/user-attachments/assets/b8ca2cfe-567c-44fc-9d46-c6168bc81eec" />
<img width="654" alt="image" src="https://github.com/user-attachments/assets/fdcf89b8-3827-460e-907f-15f716f98315" />
<br/>


## Stable Diffusion
The input that I am expecting for Dorsal will be a image of someones face and a prompt essentially telling the stable diffusion model to generate an image of the back of a persons head. To explore this image generation, I tinkered with a few things with Stable Diffusion. I first generated a couple of images using the prompt "someone turning away so you only see the back of their head" and 20 inference steps but as you might see below, there was far too much variation in the types of photos generated. A good output is something that is just the back of a persons head, something that looks somewhat true to life, and can produce an array of types of heads (i.e. different hair textures, lengths, head shapes, etc).

<br/>

<img width="1440" alt="image" src="https://github.com/user-attachments/assets/903af01e-d837-4c21-8a1d-9c0a8b0e51d5" /><br />

<br/>
<img width="1393" alt="image" src="https://github.com/user-attachments/assets/2041b10e-c2ee-46c0-b496-a460a01bcadc" />
<img width="915" alt="image" src="https://github.com/user-attachments/assets/4eaf9b5a-cbda-4f1a-902b-f50c29881628" />
<img width="978" alt="image" src="https://github.com/user-attachments/assets/102f8597-a1fe-4af3-a0af-49a04a50aae2" />
<img width="930" alt="image" src="https://github.com/user-attachments/assets/be2349c9-c393-46eb-b851-16162bc7905d" />
<br/>

While I do think that these outcomes look realistic and have a wide variety of back of head types, the second one doesn't have someones head or even torso and the last one is virtually incoherant in regards to what is trying to be depicted. I tried the same prompt with the controled random number generator and I got some of the following results.

<br/>
<img width="1093" alt="image" src="https://github.com/user-attachments/assets/70896fb1-c468-4039-a9ac-2d38aec04aa2" />
<img width="1167" alt="image" src="https://github.com/user-attachments/assets/8d9b8caf-ac0e-4632-955f-56a3458d3ac7" />
<br/>


What was interesting about this version was the consistency and accuracy of the back of the head. I generated maybe 8 different image generations at first, all of which were basically identical. The first two of the previous list of images is there as an example. I then experimented with the number of inference steps to see if I could get some variation on the realism and pinpoint a preferred number. I found that 30+ was preferrable for the type of real-life accuracy I was going for.

<br/>
<img width="1063" alt="image" src="https://github.com/user-attachments/assets/ed50f445-cc7a-460e-83b5-2e060559a734" />
<img width="1074" alt="image" src="https://github.com/user-attachments/assets/48771085-9f06-4610-a147-9668926f1162" />
<br/>

The last thing I explore that I thought the controllable random number generator was helpful for was bounding the image generated based on specific input characteristics. In the final idea of Dorsal, the input will include an image of the user so whatever replacement image is generated needs to be more controlled and mimic the nature of the original images and persons characteristics. Below are some generations with more specific visual characteristic descriptions.

<br/>
<img width="1236" alt="image" src="https://github.com/user-attachments/assets/61b55291-64ab-4385-be94-854516173954" />
<img width="1368" alt="image" src="https://github.com/user-attachments/assets/6aa33257-a998-4b6f-b18b-e34826d88cca" />
<img width="1350" alt="image" src="https://github.com/user-attachments/assets/3a3d785e-73e9-41b5-b8f5-f07c0aabe967" />
<img width="1188" alt="image" src="https://github.com/user-attachments/assets/d1fbc8c0-a059-43f3-8b97-87ab278d2560" />
<img width="1166" alt="image" src="https://github.com/user-attachments/assets/1174079b-9522-468c-bcbc-1e5cb8a372bf" />
<br/>

I tried to operationalized the prompt a bit more below just to see if I could have more control over the outputs
<br/>
<img width="1354" alt="image" src="https://github.com/user-attachments/assets/31f0242b-e33a-41d6-ae21-892616e22bda" />
<img width="1335" alt="image" src="https://github.com/user-attachments/assets/662214cf-deca-4ec0-9e0d-a92a575d016a" />
<img width="1364" alt="image" src="https://github.com/user-attachments/assets/41e4e004-4bd0-454e-934b-ae76ab0a71d2" />
<img width="1391" alt="image" src="https://github.com/user-attachments/assets/694b2cd4-97b8-4f21-bb8d-6d7d3e3dd2ad" />
<img width="1368" alt="image" src="https://github.com/user-attachments/assets/3093a230-066c-4b38-ad38-997aab3f2a7c" />
<br/>

As you can see some of these didn't follow the prompts as accuratley as I would have hoped though I wonder if given a starting image, would this process yield more accurate results?












