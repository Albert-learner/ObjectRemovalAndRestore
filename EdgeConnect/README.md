This is about Image Inpainting Model, named EdgeConnect.  
Refer this model by https://github.com/sujaykhandekar/Automated-objects-removal-inpainter and https://github.com/knazeri/edge-connect.
I conduct this model at Windows 10 and I have GTX-1660ti GPU in my machine.
If you have GPU in your machine(of course setting to use), it'll be more fasterh that using CPU.  
Download Anaconda.

1. Make Virtual Environment(I use Anaconda Prompt).
-> conda create -n (VirtualEnv_name) python=3.8.5
Use any name for VirtualEnv_name.

2. Activate Virtual Environment and install PyTorch libraries.
-> conda activate VirtualEnv_name
-> conda install pytorch==1.5.1 torchvision==0.6.1 -c pytorch

3. Go to Parent Directory and install requirements.txt.
-> cd ../
-> pip install -r requirements.txt

4. Download Pretrained EdgeConnect model and copy them in ./checkpoints directory.
   First use this command to download model.
-> bash ./scripts/download_model.sh

   I conduct test after first command, but Segmented areas are not filling. In that case,
   download one of these three pretrained model and put it at ./checkpoints directory.
   (In my case, I download places2 pretrained Edgeconnect model and it worked well.)
-> https://drive.google.com/drive/folders/1qjieeThyse_iwJ0gZoJr-FERkgD5sm4y?usp=sharing(places2)
-> https://drive.google.com/drive/folders/1nkLOhzWL-w2euo0U6amhz7HVzqNC5rqb(CelebA)
-> https://drive.google.com/drive/folders/1cGwDaZqDcqYU7kDuEbMXa9TP3uDJRBR1(Paris-street-view)

5. If you have GPU in your machine, you could quick prediction. Unless it will take long times.
   You could test images by using this command, if you have GPU in your machine.
   -> python test.py --input ./examples/my_small_data --output ./checkpoints/resultfinal -- remove 3 15

   If you don't have GPU in your machine, use this command.
   -> python test.py --input ./examples/my_small_data --output ./checkpoints/resultsfinal --remove 3 15 --cpu yes

   You can also apply Image Inpainting technique not only bird(3) and person(15) but also other objects, 
   and those are written at segmentation_classes.txt file. You can apply other class object to add 
   class number at --remove option like this,
   -> python test.py ~~~ --remove 1 2 3

   If you'd like to test your custom Images at Image Inpainting, I prefer you to put your images at 
   ./examples/my_small_data directory(In my case I make new directory at ./examples directory and it named
   test_data).
   -> python test.py --input ./examples/my_small_data
   -> python test.py --input ./examples/test_data

   And you can check the result of your Images applied to Image Inpainting technique 
   at directory that you designated(the path that behind --output).
   -> python test.py ~~~ --output ./checkpoints/resultfinal ~~
   -> python test.py ~~~ --output ./checkpoints/testfinal ~~
