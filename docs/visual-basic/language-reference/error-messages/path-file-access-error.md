---
title: "Path/File access error | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID75"
dev_langs: 
  - "VB"
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Path/File access error
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ファイル アクセス操作またはディスク アクセス操作で、オペレーティング システムがパスとファイル名を関連付けることができませんでした。  
  
### このエラーを解決するには  
  
1.  ファイル指定の形式が正しいことを確認します。  ファイル名には、絶対パスと相対パスのどちらでも指定できます。  絶対パスでは、まずドライブ名を指定し \(パスが別のドライブにある場合\)、続いてルートからファイルまでのパスを明示的に指定します。  絶対パスを指定しない場合、現在のドライブおよびディレクトリを基準にした相対パスになります。  
  
2.  保存しようとしているファイルが既存の読み取り専用ファイルを置き換えようとしていないかどうかを確認します。  既存の読み取り専用ファイルを置き換えようとしていた場合は、その既存ファイルの読み取り専用属性を変更してファイルを置き換えるか、または別のファイル名で保存します。  
  
3.  読み取り専用ファイルをシーケンシャル アクセスの `Output` モードまたは `Append` モードで開こうとしていないことを確認します。  この場合は、ファイルを `Input` モードで開くか、ファイルの読み取り専用属性を変更します。  
  
4.  データベースまたはドキュメントの中で [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プロジェクトを変更しようとしていなかったことを確認します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)