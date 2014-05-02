imperavi-elfinder
================

imperavi elfinder

Интеграция wysiwyg редактора  <a href="https://github.com/yiiext/imperavi-redactor-widget">imperavi</a>  и файлового менеджера  <a href="https://github.com/ezze/ezze-elfinder">elfinder</a>

Установка
------------

Скопировать содержимое в папку `protected/extensions`

Использование
-----

Предположим у нас есть модуль `admin`, Контроллер `PostController`, модель `Post` и view `post/edit` для модели `Post`.
Кроме этого у нас есть контроллер `FileController` в котором прописаны `action` для imperavi.

1 Пропишем `actions` для `FileController`, нас интересует action `fileUploaderConnector`

```php
public function actions()
    {
        return array(
            

			'fileUploaderConnector'=>array(
			'class'=>'application.extensions.ezzeelfinder.ElFinderConnectorAction',
			
			),
           
            
        );
    }
```


2 в view `post\edit` подключаем виджет imperavi:


```php
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

                'fmUrl'=>Yii::app()->createUrl('/admin/file/fileUploaderConnector'),
               
                


            ),
        )); 

```
3 в тоже view файле `post/edit` подключаем elfinder, для это добавляем в файл контейнер и сам виджет

```php
$this->widget("application.extensions.ezzeelfinder.ElFinderWidget", array(
    'selector' => "div#file-uploader",
    'clientOptions' => array(
        'lang' => "ru",
        'resizable' => true,
    ),
));
```
