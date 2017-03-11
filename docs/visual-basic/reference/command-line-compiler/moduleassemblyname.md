---
title: "/moduleassemblyname | Microsoft Docs"
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
  - "moduleassemblyname compiler option [Visual Basic]"
  - "/moduleassemblyname compiler option [Visual Basic]"
  - "-moduleassemblyname compiler option [Visual Basic]"
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /moduleassemblyname
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このモジュールが含まれるアセンブリの名前を指定します。  
  
## 構文  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`assembly_name`|このモジュールが含まれるアセンブリの名前。|  
  
## 解説  
 コンパイラは、`/target:module` オプションが指定された場合にのみ `/moduleassemblyname` オプションを処理します。  このとき、コンパイラによってモジュールが作成されます。  コンパイラが作成したモジュールは、`/moduleassemblyname` オプションに指定されたアセンブリでのみ有効です。  このモジュールを別のアセンブリに配置すると、ランタイム エラーが発生します。  
  
 `/moduleassemblyname` オプションは、次の条件に該当する場合にのみ必要です。  
  
-   モジュール内のデータ型が、参照先のアセンブリ内の `Friend` 型にアクセスする必要がある。  
  
-   参照先のアセンブリで、モジュールがビルドされるアセンブリに対して、フレンド アセンブリのアクセス権を認めている。  
  
 モジュールの作成の詳細については、「[\/target](../../../visual-basic/reference/command-line-compiler/target.md)」を参照してください。  フレンド アセンブリの詳細については、「[フレンド アセンブリ](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
> [!NOTE]
>  `/moduleassemblyname` オプションは、Visual Studio の開発環境からは利用できません。このオプションを利用できるのは、コマンド ライン プロンプトからコンパイルするときだけです。  
  
## 参照  
 [方法 : マルチファイル アセンブリをビルドする](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [フレンド アセンブリ](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)