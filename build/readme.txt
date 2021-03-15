作業環境: 

	Windows10 / Visual Studio 2013

方法說明:
	
	利用OpenGL，對VAO,VBO,EBO等相關function做呼叫，目的為把.bmp檔貼在.obj檔上並顯示在視窗上。
	其中在助教所提供的main.cpp裡只需修改 add_object() 與 render()，
	另外，texture部分必須修改.vert 與 .frag

操作說明:

	在add_object()中:
		
		需先生成VAO,VBO,EBO,Texture
		然後將vbo[0]綁定到GL_ARRAY_BUFFER上，
		再把shapes[0].mesh.positions.data複製到buffer中，
		最後告訴OpenGL要如何分析數據
		vbo[1],vbo[2]與以上步驟相同
		
		Texture部分在main.cpp中已經寫好，不須做任何修改

		ebo部分，與vbo雷同，相異處在於要複製的資料為mesh.indices.data

		最後再unbind vao

	在render()中:
		
		首先要把camera set設定好，使用glm::perspective()與lookAT()
		接著對object.vao進行綁定，然後繪圖，最後再unbind vao

	在.vert與.frag中:

		此部分必須添加texture，使用location = 2
		參考 https://learnopengl.com/Getting-started/Textures 做法

	完成以上步驟就能跑出預期結果。
