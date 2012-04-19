<?php
/*
Image Module 说明文档

database structure
CREATE TABLE `wm_images` (
  `id` int(10) NOT NULL AUTO_INCREMENT,
  `image_name` varchar(64) DEFAULT NULL,
  `image_type` varchar(4) DEFAULT NULL,
  `user_guid` int(10) unsigned DEFAULT NULL,
  `create_type` varchar(16) DEFAULT 'temp',
  `entity_guid` int(10) unsigned DEFAULT '0',
  `time_created` int(11) DEFAULT NULL,
  `orig_name` varchar(64) DEFAULT NULL,
  `relative_path` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;


-----------
Controller 
    --------------------------------------------------------------------------------------------
    method 
        function upload_image_to_tmp($upload_config,$img_config){...}
        上传图片至lin临时目录()

    segment
        $upload_config CI上传类的配置数组 可设置的值参考 http://codeigniter.com/user_guide/libraries/file_uploading.html 的 Reference Guide
        $img_config 上传图片的相关配置
            $img_config['userfile'] 表单file类型input的name值，默认为'userfile'

    return array
        $result = array(
            'error' => 记录上传出现的错误，没有错误则为空
            'data'  => 上传至临时目录的图片信息，如果error为空则存在该数据
        )


    --------------------------------------------------------------------------------------------
    method 
        function upload_image($upload_config,$img_config,$img_data){...}
        上传单张图片,无ajax效果，内部调用 upload_image_to_tmp 实现完整过程

    segment
        $upload_config CI上传类的配置数组 可设置的值参考 http://codeigniter.com/user_guide/libraries/file_uploading.html 的 Reference Guide
        $img_config 上传图片的相关配置
            $img_config['relative_path'] 图片上传的相对路径
            $img_config['destination'] 图片上传的目录(要求可读可写)
            $img_config['userfile'] 表单file类型input的name值，默认为'userfile'
        $img_data 图片存入数据库需要记录的数据
            $img_data['entity_guid'] 图片对应的entity_guid
            $img_data['create_type'] 图片在系统中所属的类型
            $img_data['user_guid']  用户ID

    return array
        $result = array(
            'error' => 记录上传出现的错误，没有错误则为空
            'id'    => 图片记录的id
        );

    --------------------------------------------------------------------------------------------
    method
        function delete_image($image_id)
        删除指定图片

    segment
        $image_id 图片记录的id

    return bool
        $result 删除是否成功

    --------------------------------------------------------------------------------------------
    method
        function get_image_path($image_id){...}
        获取图片路径

    segment
        $image_id 图片记录的id

    return string
        $path; 图片的绝对路径（如果常量 IMG_ABSOLUTE_PATH 的值为".",返回的是相对路径，方便开发）


    --------------------------------------------------------------------------------------------
    method
        function upload_avatar_image($data,$img_config,$img_data)
        上传头像（需要图片已上传至临时目录）

    segment
        $data   临时目录中的头像图片信息
        $img_config 上传图片的相关配置
            $img_config['size'] 图片需要缩放的大小数组 例: array(array('w'=>30,'h'=>30),array('w'=>60,'h'=>60),array('w'=>90,'h'=>90))
            $img_config['x'] 裁剪的横坐标
            $img_config['y'] 裁剪的纵坐标
            $img_config['w'] 裁剪的宽度
            $img_config['h'] 裁剪的高度
        $img_data 存储过程需要的信息
            $img_data['unique_id'] 用户的unique_id,创建用户目录用

    return array
    $result = array(
        'error' => 记录错误信息，没有错误则为空
    )


----------
Model

----------
View
 */
?>
