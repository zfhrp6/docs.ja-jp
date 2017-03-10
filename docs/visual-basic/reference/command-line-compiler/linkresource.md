---
title: "/linkresource (Visual Basic) | Microsoft Docs"
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
  - "/linkresource compiler option [Visual Basic]"
  - "-linkresource compiler option [Visual Basic]"
  - "linkresource compiler option [Visual Basic]"
  - "/linkres compiler option [Visual Basic]"
  - "linkres compiler option [Visual Basic]"
  - "-linkres compiler option [Visual Basic]"
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /linkresource (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

マネージ リソースへのリンクを作成します。  
  
## 構文  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## 引数  
 `filename`  
 必ず指定します。  アセンブリにリンクするリソース ファイルです。  ファイル名に空白が含まれる場合、ファイル名を引用符 \(" "\) で囲みます。  
  
 `identifier`  
 省略可能です。  リソースの論理名です。  リソースを読み込むために使用する名前です。  既定値はファイル名です。  オプションとして、ファイルがアセンブリ マニフェスト内でパブリックかプライベートかを指定できます \(例: `/linkres:filename.res,myname.res,public`\)。  既定では、`filename` はアセンブリ内でパブリックです。  
  
## 解説  
 `/linkresource` オプションは、リソース ファイルを出力ファイルに埋め込みません。リソース ファイルを出力ファイルに埋め込むには、`/resource` オプションを使用してください。  
  
 `/linkresource` オプションでは、`/target:module` 以外のいずれかの `/target` オプションが必要です。  
  
 たとえば、`filename` が [Resgen.exe \(リソース ファイル ジェネレーター\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) または開発環境で作成された [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] リソース ファイルである場合は、<xref:System.Resources> 名前空間のメンバーを使用してアクセスできます。  詳細については、「<xref:System.Resources.ResourceManager>」を参照してください。実行時にその他のすべてのリソースにアクセスするには、<xref:System.Reflection.Assembly> クラスで `GetManifestResource` で始まるメソッドを使用します。  
  
 ファイル名はどのようなファイル形式でもかまいません。  たとえば、ネイティブ DLL をアセンブリの一部として含め、そのネイティブ DLL をグローバル アセンブリ キャッシュにインストールして、アセンブリ内のマネージ コードからアクセスできるようにすることもできます。  
  
 `/linkres` は `/linkresource` の省略形です。  
  
> [!NOTE]
>  `/linkresource` オプションは Visual Studio の開発環境からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 次に、`In.vb` をコンパイルしてリソース ファイル `Rf.resource` にリンクする場合のコード例を示します。  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)