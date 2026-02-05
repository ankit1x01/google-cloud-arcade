```
cat <<'EOF' > GenerateImage.py
import vertexai
from vertexai.vision_models import ImageGenerationModel

def generate_image(prompt):
    # Initialize Vertex AI
    vertexai.init(project="YOUR_PROJECT_ID", location="us-central1")

    # Load the specific Imagen 3 model version
    model = ImageGenerationModel.from_pretrained("imagen-3.0-generate-002")

    # Generate the image
    response = model.generate_images(
        prompt=prompt,
        number_of_images=1,
        add_watermark=True
    )

    # Save the first generated image to the local directory
    response[0].save(location="image.jpeg", include_generation_parameters=False)
    print("Image saved as image.jpeg")

# Execute the function with the required prompt
if __name__ == "__main__":
    prompt_text = "Create an image of a cricket ground in the heart of Los Angeles"
    generate_image(prompt_text)
EOF

/usr/bin/python3 /GenerateImage.py
```


(Note: Replace "YOUR_PROJECT_ID" with your actual Google Cloud Project ID if it isn't pre-configured.)


