---
title: "/keyfile | Microsoft Docs"
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
  - "/keyfile compiler option [Visual Basic]"
  - "keyfile compiler option [Visual Basic]"
  - "-keyfile compiler option [Visual Basic]"
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /keyfile
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

アセンブリに厳密な名前を付けるキーおよびキー ペアを含むファイルを指定します。  
  
## 構文  
  
```  
/keyfile:file  
```  
  
## 引数  
 `file`  
 必ず指定します。  キーを含むファイル。  ファイル名に空白が含まれる場合、ファイル名を引用符 \(" "\) で囲みます。  
  
## 解説  
 コンパイラが、アセンブリ マニフェストに公開キーを挿入し、秘密キーを使用して最後のアセンブリに署名します。  キー ファイルを生成するには、コマンド ラインで「`sn -k file`」と入力します。  詳細については、「[Sn.exe \(厳密名ツール\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)」を参照してください。  
  
 `/target:module` を使用してコンパイルすると、キー ファイル名はモジュールに保持され、[\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) でアセンブリをコンパイルするときに作成されるアセンブリに組み込まれます。  
  
 [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) を使用して、暗号に関する情報をコンパイラに渡すこともできます。  部分署名されたアセンブリを作成する場合は、[\/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) を使用します。  
  
 このオプションは、任意の Microsoft Intermediate Language \(MSIL\) モジュールのソース コードでカスタム属性 \(<xref:System.Reflection.AssemblyKeyFileAttribute>\) として指定することもできます。  
  
 コマンド ライン オプションまたはカスタム属性によって、コンパイル時に `/keyfile` と [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) の両方が同時に指定されると、コンパイラは先にキー コンテナーを処理します。  コンテナーが検出された場合、アセンブリはキー コンテナーの情報で署名されます。  キー コンテナーを検出できなかった場合、コンパイラは `/keyfile` で指定されたファイルを検索します。  キー ファイルが見つかった場合は、そのファイル内の情報を使用してアセンブリに署名され、次のコンパイル時にキー コンテナーが有効になるように、キー情報がキー コンテナーに組み込まれます \(`sn -i` と同様\)。  
  
 キー ファイルには、公開キーだけが含まれていることがあります。  
  
 アセンブリに対する署名の詳細については、「[厳密な名前付きアセンブリの作成と使用](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)」を参照してください。  
  
> [!NOTE]
>  `/keyfile` オプションは [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 開発環境内では利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 ソース ファイル `Input.vb` をコンパイルし、キー ファイルを指定する場合のコード例です。  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## 参照  
 [アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)