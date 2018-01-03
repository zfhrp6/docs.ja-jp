---
title: "イベント ログに無効な名前が指定されました"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76e4082710a6786ec5e743ce606e849637c26512
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>イベント ログに無効な名前が指定されました
イベント ログに無効な名前が指定されました。 通常これは、名前に含まれる無効な文字、空のファイル名、または長すぎるファイル名の結果です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   指定した名前が 8 文字を超える場合、他のイベント ログの名前と競合しないことを確認します。 名前が一意であるかどうかを判断するときには、最初の 8 文字のみが評価されます。  
  
-   パスを指定する場合は、正しく解析されることを確認します。  
  
-   名前に無効な文字がないことを確認してください。 ファイル名に使用できない文字には `<`、 `>`、 `:`、 `"`、 `/`、 `\`、および `|`があります。  
  
## <a name="see-also"></a>参照  
 [方法: ファイル パスを解析する](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [方法: ファイルの名前を変更する](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 
