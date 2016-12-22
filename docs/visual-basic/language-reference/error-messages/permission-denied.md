---
title: "Permission denied (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID70"
dev_langs: 
  - "VB"
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Permission denied (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

書き込もうとしているディスクが書き込み保護されているか、またはアクセスしようとしているファイルがロックされています。  
  
### このエラーを解決するには  
  
1.  書き込み保護されているファイルを開くには、ファイルの書き込み保護属性を変更します。  
  
2.  他のプロセスによってファイルがロックされていないかどうかを確認し、ロックされていた場合は、解放されるまで待ってからファイルを開きます。  
  
3.  レジストリにアクセスするには、自分のユーザー アクセス許可で、この種のレジストリ アクセスが可能であることを確認します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)