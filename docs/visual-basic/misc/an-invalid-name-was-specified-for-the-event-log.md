---
title: "イベント ログに無効な名前が指定されました | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# イベント ログに無効な名前が指定されました
イベント ログに無効な名前が指定されました。 通常これは、名前に含まれる無効な文字、空のファイル名、または長すぎるファイル名の結果です。  
  
### このエラーを解決するには  
  
-   指定した名前が 8 文字を超える場合、他のイベント ログの名前と競合しないことを確認します。 名前が一意であるかどうかを判断するときには、最初の 8 文字のみが評価されます。  
  
-   パスを指定する場合は、正しく解析されることを確認します。  
  
-   名前に無効な文字がないことを確認してください。 ファイル名に使用できない文字には `<`、`>`、`:`、`"`、`/`、`\`、および `|` があります。  
  
## 参照  
 [方法 : ファイル パスを解析する](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)   
 [How to: Rename a File](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)   
 [How to: Create and Remove Custom Event Logs](http://msdn.microsoft.com/ja-jp/af9b7da0-80c7-46ac-b7f7-897063ddd503)