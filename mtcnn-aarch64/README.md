# mtcnn-pytorch

# Test an image
  * python3 mtcnn_test.py
 
# Training data prepraring
  * download [WIDER Face Training Images](http://shuoyang1213.me/WIDERFACE/) face detection data(WIDER_train.zip), then store it into data_set/face_detection/WIDERFACE/WIDER_train, unzip the tar ball file  
  * download [Face annotations](http://shuoyang1213.me/WIDERFACE/) face split data(wider_face_split.zip), then store it into data_set/face_detection/WIDERFACE/wider_face_split, unzip the tar ball file  
    * python3 ./anno_store/tool/format/transform.py change .mat into .txt(issue with 54_Rescue_rescuepeople_54_29.jpg, delete this resource from the result, and this step is not necessary, .txt file already committed)  
  * download [CNN_FacePoint](http://mmlab.ie.cuhk.edu.hk/archive/CNN_FacePoint.htm) face detection and landmark data(train.zip), then store it into data_set/face_landmark/CNN_FacePoint/train, unzip the tar ball file  

# Training
  * preparing data for P-Net
    * python3 mtcnn/data_preprocess/gen_Pnet_train_data.py
    * python3 mtcnn/data_preprocess/assemble_pnet_imglist.py
  * train P-Net
    * python3 mtcnn/train_net/train_p_net.py
    
  * preparing data for R-Net
    * python3 mtcnn/data_preprocess/gen_Rnet_train_data.py
    * python3 mtcnn/data_preprocess/assemble_rnet_imglist.py
  * train R-Net
    * python3 mtcnn/train_net/train_r_net.py
  
  * preparing data for O-Net
    * python3 mtcnn/data_preprocess/gen_Onet_train_data.py
    * python3 mtcnn/data_preprocess/gen_landmark_48.py
    * python3 mtcnn/data_preprocess/assemble_onet_imglist.py
  * train O-Net
    * python3 mtcnn/train_net/train_o_net.py
