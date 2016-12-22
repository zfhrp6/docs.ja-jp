---
title: "/reference (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/reference compiler option [Visual Basic]"
  - "r compiler option [Visual Basic]"
  - "-reference compiler option [Visual Basic]"
  - "/r compiler option [Visual Basic]"
  - "reference compiler option [Visual Basic]"
  - "-r compiler option [Visual Basic]"
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定のアセンブリ内の型情報をコンパイル中のプロジェクトで使用できるようにします。  
  
## 構文  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`fileList`|必ず指定します。  アセンブリのファイル名をコンマで区切ったリストです。  ファイル名に空白が含まれる場合は、二重引用符 \(" "\) で囲む必要があります。|  
  
## 解説  
 インポートするファイルは、アセンブリ メタデータを含んでいる必要があります。  アセンブリの外側ではパブリックな型だけが参照できます。  [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) は、モジュールからメタデータをインポートします。  
  
 別のアセンブリ \(Assembly B\) を参照するアセンブリ \(Assembly A\) を参照するときに、アセンブリ B も参照する必要があるのは、次の場合です。  
  
-   アセンブリ A の型がアセンブリ B の型を継承しているか、アセンブリ B のインターフェイスを実装している場合。  
  
-   アセンブリ B の戻り値の型やパラメーターの型を持つフィールド、プロパティ、イベント、またはメソッドを呼び出す場合。  
  
 [\/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) を使用して、1 つ以上のアセンブリ参照があるディレクトリを指定します。  
  
 コンパイラが \(モジュールではなく\) アセンブリ内の型を認識するためには、その型をコンパイラに解決させる必要があります。  これには、たとえばその型のインスタンスを定義するなどの方法があります。  コンパイラのためにアセンブリ内の型名を解決する方法は他にもあります。  たとえば、アセンブリ内の型を継承すると、コンパイラはその型名を認識できるようになります。  
  
 既定では、頻繁に使用される [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] アセンブリを参照する Vbc.rsp 応答ファイルが使用されます。  コンパイラで Vbc.rsp を使用しない場合は、`/noconfig` を使用します。  
  
 `/reference` の省略形は `/r` です。  
  
## 使用例  
 ソース ファイル I`nput.vb` と、M`etad1.dll` および M`etad2.dll` からの参照アセンブリをコンパイルし、O`ut.exe` を生成する場合のコード例です。  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)