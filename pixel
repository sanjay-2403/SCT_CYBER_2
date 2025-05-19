from PIL import Image
import random

def encrypt_image(image_path, output_path, key):
    """
    Encrypts an image by applying a basic mathematical operation to each pixel.
    
    :param image_path: Path to the input image
    :param output_path: Path to save the encrypted image
    :param key: Integer key used for encryption
    """
    image = Image.open(image_path)
    pixels = list(image.getdata())
    encrypted_pixels = []

    for pixel in pixels:
        if isinstance(pixel, int):  # Grayscale image
            encrypted_pixels.append((pixel + key) % 256)
        else:  # RGB or RGBA image
            encrypted_pixels.append(tuple((value + key) % 256 for value in pixel))

    encrypted_image = Image.new(image.mode, image.size)
    encrypted_image.putdata(encrypted_pixels)
    encrypted_image.save(output_path)
    print(f"Image encrypted and saved to {output_path}")


def decrypt_image(image_path, output_path, key):
    """
    Decrypts an image by reversing the encryption operation.
    
    :param image_path: Path to the encrypted image
    :param output_path: Path to save the decrypted image
    :param key: Integer key used for decryption
    """
    image = Image.open(image_path)
    pixels = list(image.getdata())
    decrypted_pixels = []

    for pixel in pixels:
        if isinstance(pixel, int):  # Grayscale image
            decrypted_pixels.append((pixel - key) % 256)
        else:  # RGB or RGBA image
            decrypted_pixels.append(tuple((value - key) % 256 for value in pixel))

    decrypted_image = Image.new(image.mode, image.size)
    decrypted_image.putdata(decrypted_pixels)
    decrypted_image.save(output_path)
    print(f"Image decrypted and saved to {output_path}")


def main():
    print("Welcome to the Simple Image Encryption Tool!")
    choice = input("Would you like to 'encrypt' or 'decrypt' an image? ").strip().lower()

    if choice not in ['encrypt', 'decrypt']:
        print("Invalid choice. Please select 'encrypt' or 'decrypt'.")
        return

    image_path = input("Enter the path to the image: ").strip()
    output_path = input("Enter the path to save the output image: ").strip()
    key = input("Enter an integer key for encryption/decryption: ").strip()

    try:
        key = int(key)
    except ValueError:
        print("The key must be an integer.")
        return

    if choice == 'encrypt':
        encrypt_image(image_path, output_path, key)
    elif choice == 'decrypt':
        decrypt_image(image_path, output_path, key)
    else:
        print("Invalid choice. Please select 'encrypt' or 'decrypt'.")

if __name__ == "__main__":
    main()