# mtcnn-pytorch

# Test an image
  * python3 mtcnn_test.py
 
# Training data prepraring
  * download [WIDER FACE](https://pan.baidu.com/s/1sJTO7TcQ2576RUqR_IIhbQ) (passcode:lsl3) face detection data then store it into ./data_set/face_detection
    * python3 ./anno_store/tool/format/transform.py change .mat(wider_face_train.mat) into .txt(anno_train.txt)
  * download [CNN_FacePoint](http://mmlab.ie.cuhk.edu.hk/archive/CNN_FacePoint.htm) face detection and landmark data then store it into ./data_set/face_landmark

# Training
  * preparing data for P-Net
    * python3 mtcnn/data_preprocess/gen_Pnet_train_data.py
    * python3 mtcnn/data_preprocess/assemble_pnet_imglist.py
  * train P-Net
    * python3 mtcnn/train_net/train_p_net.py
    
  * preparing data for R-Net
    * python3 mtcnn/data_preprocess/gen_Rnet_train_data.py (maybe you should change the pnet model path)
    * python3 mtcnn/data_preprocess/assemble_rnet_imglist.py
  * train R-Net
    * python3 mtcnn/train_net/train_r_net.py
  
  * preparing data for O-Net
    * python3 mtcnn/data_preprocess/gen_Onet_train_data.py
    * python3 mtcnn/data_preprocess/gen_landmark_48.py
    * python3 mtcnn/data_preprocess/assemble_onet_imglist.py
  * train O-Net
    * python3 mtcnn/train_net/train_o_net.py
