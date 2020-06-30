# TensorFlow_images_classification

## Commandes à executer avant de commencer :

IMAGE_SIZE=224
ARCHITECTURE="mobilenet_0.50_${IMAGE_SIZE}"

## Lancer un apprentissage : 

python -m scripts.retrain \
  --bottleneck_dir=tf_files/bottlenecks \
  --how_many_training_steps=500 \
  --model_dir=tf_files/models/ \
  --summaries_dir=tf_files/training_summaries/"${ARCHITECTURE}" \
  --output_graph=tf_files/retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --architecture="${ARCHITECTURE}" \
  --image_dir=tf_files/images

## Reconnaître une image donnée :

python -m scripts.label_image \
    --graph=tf_files/retrained_graph.pb  \
    --image=tf_files/images/paquerettes/21652746_cc379e0eea_m.jpg
