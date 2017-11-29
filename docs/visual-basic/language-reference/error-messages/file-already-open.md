---
title: "ファイルは既に開かれています。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a>ファイルは既に開かれています。
別の前に、ファイルを閉じる必要がある場合もあります`FileOpen`またはその他の操作が発生することができます。 このエラーでは以下の原因が考えられます。  
  
-   連続した出力モード`FileOpen`操作が既に開いているファイルに対して実行されました。  
  
-   ステートメントは、開いているファイルを参照します。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  ステートメントを実行する前に、ファイルを閉じます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
