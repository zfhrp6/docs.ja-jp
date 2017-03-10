---
title: "/resource (Visual Basic) | Microsoft Docs"
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
  - "/resource compiler option [Visual Basic]"
  - "-resource compiler option [Visual Basic]"
  - "/res compiler option [Visual Basic]"
  - "res compiler option [Visual Basic]"
  - "-res compiler option [Visual Basic]"
  - "resource compiler option [Visual Basic]"
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# /resource (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

マネージ リソースをアセンブリに埋め込みます。  
  
## 構文  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`filename`|必ず指定します。  出力ファイルに埋め込むリソース ファイルの名前。  既定では、`filename` はアセンブリ内でパブリックです。  ファイル名に空白が含まれている場合は、二重引用符 \(" "\) で囲みます。|  
|`identifier`|省略可能です。  リソースの論理名。リソースを読み込むときに使用します。  既定値はファイル名です。  オプションとして、`/res:``filename.res`、`myname.res`、`public` では、リソースがアセンブリ マニフェスト内でパブリックかプライベートかを指定できます。|  
  
## 解説  
 リソース ファイルを出力ファイルに組み込まずにリソースをアセンブリにリンクするには、`/linkresource` オプションを使用します。  
  
 たとえば、`filename` が [Resgen.exe \(リソース ファイル ジェネレーター\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) または開発環境で作成された [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] リソース ファイルである場合は、<xref:System.Resources> 名前空間のメンバーを使用してアクセスできます。詳細については、「<xref:System.Resources.ResourceManager>」を参照してください。  実行時に他のすべてのリソースにアクセスするには、<xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>、<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>、または<xref:System.Reflection.Assembly.GetManifestResourceStream%2A> のいずれかのメソッドを使用します。  
  
 `/res` は `/resource`  の省略形です。  
  
 設定する方法の詳細については`/resource` Visual Studio の IDE を参照してください[アプリケーション リソースの管理 \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet)。  
  
## 使用例  
 `In.vb` をコンパイルし、リソース ファイル `Rf.resource` をアタッチする場合のコード例です。  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)   
 [\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)