---
title: "/addmodule | Microsoft Docs"
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
  - "/addmodule compiler option [Visual Basic]"
  - "addmodule compiler option [Visual Basic]"
  - "-addmodule compiler option [Visual Basic]"
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# /addmodule
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定ファイルからのすべての型情報をコンパイル中のプロジェクトで使用できるようにします。  
  
## 構文  
  
```  
/addmodule:fileList  
```  
  
## 引数  
 `fileList`  
 必ず指定します。  メタデータは含まれるが、アセンブリ マニフェストは含まれないファイルの、コンマ区切りのリストです。  空白を含むファイル名は、引用符 \(" "\) で囲みます。  
  
## 解説  
 `fileList` パラメーターで表示されるファイルは、`/target:module` オプション \(または他のコンパイラで `/target:module` に相当するオプション\) を指定して作成する必要があります。  
  
 `/addmodule` を使用して追加されたすべてのモジュールは、実行時に出力ファイルと同じディレクトリに配置されている必要があります。  つまり、コンパイル時にはどのディレクトリのモジュールでも指定できますが、実行時にはモジュールをアプリケーション ディレクトリに置く必要があります。  アプリケーション ディレクトリにモジュールがないと、<xref:System.TypeLoadException> エラーが発生します。  
  
 `/target:module` 以外の [\/target](../../../visual-basic/reference/command-line-compiler/target.md) オプションを `/addmodule` と共に暗黙的または明示的に指定すると、`/addmodule` に渡すファイルはプロジェクトのアセンブリの一部になります。  アセンブリは、`/addmodule` で追加されたファイルを 1 つ以上含む出力ファイルを実行する必要があります。  
  
 アセンブリを含むファイルからメタデータをインポートするには、[\/reference](../../../visual-basic/reference/command-line-compiler/reference.md) を使用します。  
  
> [!NOTE]
>  `/addmodule` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 モジュールを作成する場合のコード例を次に示します。  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/visualbasic/addmodule_1.vb)]  
  
 モジュールの型をインポートする場合のコード例を次に示します。  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/visualbasic/addmodule_2.vb)]  
  
 `t1` を実行すると、`802` が出力されます。  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)