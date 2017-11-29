---
title: "ファイルにこれ以上データがありません。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27de462d5d28ee09107d75afe8269e7401c4dc39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="input-past-end-of-file"></a>ファイルにこれ以上データがありません。
いずれか、`Input`ステートメントは、空であるファイルまたはすべてのデータを使用すると、またはを使用して 1 つから読み取っている、`EOF`ファイルを使用して関数がバイナリ用に開かれています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  使用して、`EOF`関数の直前に、`Input`ステートメント ファイルの終わりを検出します。  
  
2.  ファイルがバイナリ アクセスで開かれている場合を使用して`Seek`と`Loc`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
