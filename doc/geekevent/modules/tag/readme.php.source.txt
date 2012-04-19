<?php
/*
Tag Module 说明文档

database structure
CREATE TABLE `tag_relations` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `tag_id` int(11) DEFAULT NULL,
  `entity_guid` int(11) DEFAULT NULL,
  `type` varchar(32) DEFAULT NULL,
  `time_created` int(11) DEFAULT NULL,
  `user_guid` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;


-----------
Controller 
    --------------------------------------------------------------------------------------------
    method 
        function add_tag_relation($entity_guid,$tag_name,$relation_type,$user_guid){...}
        插入标签与对应entity的关系，如果标签不存在则创建

    segment
        $entity_guid    entity的ID
        $tag_name       标签内容   
        $relation_type  entity类型，记录标签与entity的关系类型
        $user_guid      插入关系的用户ID

    return string
        $error          返回的错误信息，如果没有则为空


    --------------------------------------------------------------------------------------------
    method
        function delete_tag_relation($entity_guid,$tag_name){...}
        删除标签与对应entity关系

    segment
        $entity_guid    entity的ID
        $tag_name       标签内容

    return string
        $error          返回的错误信息，如果没有则为空

----------
Model
    --------------------------------------------------------------------------------------------
    method
        function does_tag_exist($tag_name){...}
        判断标签是否存在

    segment
        $tag_name       标签内容

    return object/bool
        $result         如果存在则返回core_entity相应记录,如果不存在则返回FALSE


    --------------------------------------------------------------------------------------------
    method
        function does_relation_exist($tag_id,$entity_guid){...}
        判断标签与对应entity关系是否存在

    segment
        $tag_id         标签ID
        $entity_guid    entity的ID

    return  bool
        $result         关系存在返回TURE，否则返回FALSE

----------
View

 */
?>
