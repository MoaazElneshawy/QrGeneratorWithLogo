# QrGeneratorWithLogo
Generate Qr Code using ZXING with a logo if needed

Download the Helper file and use it

1- add zxing lib into your project

      implementation 'com.google.zxing:core:3.4.0'
      
2- use the helper methods 

	     try {
			 val content = "www" // add your content here

			 try {
				 val displayMetrics = DisplayMetrics()
				 context.windowManager.defaultDisplay?.getMetrics(displayMetrics)

					val size = displayMetrics.widthPixels.coerceAtMost(displayMetrics.heightPixels)

					val overlay = context.getDrawableCompat(R.drawable.app_icon)
										?.toBitmap(100.dpToPx(), 100.dpToPx())

					val bitmap = content.encodeAsQrCodeBitmap(
								size,
								overlay,
								context.getColorCompat(R.color.hj_color_blue),
								context.getColorCompat(android.R.color.white)
							)
					bitmap?.let {imageView.setImageBitmap(it)} // replace imageView with your view
						
          } catch (e: Exception) {
							e.printStackTrace()
					}      

