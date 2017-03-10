---
title: "/keycontainer | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-keycontainer compiler option [Visual Basic]"
  - "keycontainer compiler option [Visual Basic]"
  - "/keycontainer compiler option [Visual Basic]"
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /keycontainer
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

アセンブリに厳密な名前を付けるために、キー ペアのキー コンテナーの名前を指定します。  
  
## 構文  
  
```  
/keycontainer:container  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`container`|必ず指定します。  キーを含むコンテナー ファイル。  ファイル名に空白が含まれる場合は、二重引用符 \(" "\) で囲む必要があります。|  
  
## 解説  
 コンパイラでは、アセンブリ マニフェストに公開キーを挿入し、秘密キーを使用して最後のアセンブリに署名することによって、共有可能コンポーネントが作成されます。  キー ファイルを生成するには、コマンド ラインで「`sn -k` `file`」と入力します。  `-i`  オプションを使用すると、キー ペアがコンテナーにインストールされます。  詳細については、「[Sn.exe \(厳密名ツール\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)」を参照してください。  
  
 `/target:module` を使用してコンパイルすると、キー ファイル名はモジュールに保持され、[\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) でアセンブリをコンパイルするときに作成されるアセンブリに組み込まれます。  
  
 このオプションは、任意の Microsoft Intermediate Language \(MSIL\) モジュールのソース コードで、カスタム属性 \(<xref:System.Reflection.AssemblyKeyNameAttribute>\) として指定することもできます。  
  
 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) を使用して、暗号に関する情報をコンパイラに渡すこともできます。  部分署名されたアセンブリを作成する場合は、[\/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) を使用します。  
  
 アセンブリに対する署名の詳細については、「[厳密な名前付きアセンブリの作成と使用](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)」を参照してください。  
  
> [!NOTE]
>  `/keycontainer` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 ソース ファイル `Input.vb` をコンパイルし、キー コンテナーを指定する場合のコード例です。  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## 参照  
 [アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)