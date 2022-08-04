def get_image_char_picture(picture_path, saving_path, font_size=10, font_path=r"C:\Windows\Fonts\STKAITI.ttf"):
    ascii_char = list("$@B%8&WM#*oahkbdpqwmZO0QLCJUYXzcvunxrjft/\\|()1{}[]?-_+~<>i!lI;:,\"^`'. ")
    img = Image.open(picture_path)
    img_src = numpy.array(img.convert("RGBA"))
    w, h = img.size
    saving_img = Image.new("RGBA", (w, h))
    draw = ImageDraw.Draw(saving_img)
    font = ImageFont.truetype(font_path, font_size)
    img_format = saving_path.split('.')[-1]
    if img_format != "png":
        raise(RuntimeError("function get_image_char_picture can only save a picture as png, but not " + img_format))
    for i in range(0, h, int(font_size / 2)):
        for j in range(0, w, int(font_size / 2)):
            r, g, b, a = img_src[i][j]
            grey = (2126 * r + 7152 * g + 722 * b) / 10000
            if grey > 250:
                char = " "
            else:
                char = ascii_char[int(grey / len(ascii_char))]
            draw.text((j, i), char, fill=(r, g, b, a), font=font)
    saving_img.save(saving_path)
