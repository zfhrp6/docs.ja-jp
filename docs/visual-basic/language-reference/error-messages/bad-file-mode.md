---
title: "Bad file mode | Microsoft Docs"
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
  - "vbrID54"
dev_langs: 
  - "VB"
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Bad file mode
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ファイルの内容を操作するステートメントは、ファイルを開くときに指定したモードに対応している必要があります。  以下の原因が考えられます。  
  
-   `FilePutObject` ステートメントまたは `FileGetObject` ステートメントでシーケンシャル ファイルを指定しています。  
  
-   `Print` ステートメントで、`Output` または `Append` 以外のアクセス モードで開いたファイルを指定しています。  
  
-   `Input` ステートメントで、`Input` 以外のアクセス モードで開いたファイルを指定しています。  
  
-   読み取り専用のファイルに書き込みを行おうとしました。  
  
### このエラーを解決するには  
  
-   `FilePutObject` や `FileGetObject` で参照されているファイルが、`Random` アクセスまたは `Binary` アクセスで開いたファイルだけであることを確認します。  
  
-   `Print` で `Output` アクセス モードまたは `Append` アクセス モードで開いたファイルを指定します。  そうでない場合は、別のステートメントを使ってファイルにデータを書き込むか、ファイルを適切なモードで開き直します。  
  
-   `Input` に `Input` で開いたファイルを指定します。  そうでない場合は、別のステートメントを使ってファイルにデータを書き込むか、ファイルを適切なモードで開き直します。  
  
-   読み取り専用ファイルに書き込んでいる場合は、ファイルの読み取り\/書き込み属性を変更するか、そのファイルに書き込まないようにします。  
  
-   `My.Computer.FileSystem` オブジェクトで準備されている機能を使用します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileSystem>   
 [Troubleshooting: Reading from and Writing to Text Files](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)