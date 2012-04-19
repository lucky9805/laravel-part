<?php
/*
Comment Module 说明文档

database structure
CREATE TABLE `comments` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `guid` int(11) DEFAULT NULL,
  `entity_guid` int(11) NOT NULL,
  `fid` int(11) NOT NULL DEFAULT '0',
  `vote` int(11) NOT NULL DEFAULT '0',
  `user_guid` int(11) DEFAULT NULL,
  `time_created` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

-----------
Controller 
    --------------------------------------------------------------------------------------------
    method 
        function add_comment($entity_guid,$fid=0,$content,$user_guid,$source='web'){...}
        添加评论

    segment
        $entity_guid    评论针对的entity ID
        $fid            评论针对的评论
        $content        评论内容
        $user_guid      发表评论的用户ID
        $source         发表评论的方式

    return bool/int
        $result         插入失败则返回FALSE，否则返回生成的评论ID


----------
Model

----------
View

 */
?>
