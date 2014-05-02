imperavi-elfinder
================

imperavi elfinder

Интеграция wysiwyg редактора  <a href="https://github.com/yiiext/imperavi-redactor-widget">imperavi</a>  и файлового менеджера  <a href="https://github.com/ezze/ezze-elfinder">elfinder</a>

Установка
------------

Скопировать содержимое в папку `protected/extensions`

2 Подлкючение imperavi редактора

<?php
		 
 $this->widget('ImperaviRedactorWidget', array(
            // You can either use it for model attribute
            'model' => $model,
            'attribute' => 'text',

            'plugins' => array(
                'fontfamily' => array(
                'js' => array('fontfamily.js',),
                ),
                 'fontcolor' => array(
                'js' => array('fontcolor.js',),
                ),
                 'fontsize' => array(
                'js' => array('fontsize.js',),
                ),
                'fullscreen' => array(
                'js' => array('fullscreen.js',),
                ),
                 'extelf' => array(
                'js' => array('extelf.js',),
                ),

               
                
                ),


            'options'=>array(
                
                'buttons'=>array(
                    'formatting', '|', 'bold', 'italic', 'deleted', '|',
                    'unorderedlist', 'orderedlist', 'outdent',  'indent', 'alignment', 'table','horizontalrule', '|',
                    'image', 'video', 'file', 'link',  '|', 'html',
                ),
                'lang'=>'ru',
                'rows'=> '2',
                'minHeight' => 300,
                'thumbLinkClass'=>'athumbnail', //Класс по-умолчанию для ссылки на полное изображение вокруг thumbnail
                'thumbClass'=>'thumbnail pull-left', //Класс по-умолчанию для  thumbnail
                'defaultUplthumb'=>true, //Вставлять по-умолчанию после загрузки превью? если нет - полное изображение
                // 'iframe' => true,
                'toolbar' => true,

                'fileUpload'=>Yii::app()->createUrl('/admin/file/fileUpload',array(
                'attr'=>$attribute
                )),
                'fileUploadErrorCallback'=>new CJavaScriptExpression(
                'function(obj,json) { alert(json.error); }'
                ),
                'imageUpload'=>Yii::app()->createUrl('/admin/file/imageUpload',array(
                'attr'=>$attribute
                )),
                'imageGetJson'=>Yii::app()->createUrl('/admin/file/imageList',array(
                'attr'=>$attribute
                )),
                'imageUploadErrorCallback'=>new CJavaScriptExpression(
                'function(obj,json) { alert(json.error); }'
                ),
                // 'shortcuts'=>'true',
                // 'cleanup'=>true,
               
                'fmUrl'=>Yii::app()->createUrl('/admin/file/fileUploaderConnector'),
               
                


            ),
        )); 


		 ?>
