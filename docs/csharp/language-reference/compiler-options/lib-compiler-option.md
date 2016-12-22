---
title: "/lib (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/lib"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lib compiler option [C#]"
  - "-lib compiler option [C#]"
  - "/lib compiler option [C#]"
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /lib (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/lib** オプションでは、[\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) オプションによって参照されるアセンブリの場所を指定します。  
  
## 構文  
  
```  
/lib:dir1[,dir2]  
```  
  
## Arguments  
 `dir1`  
 参照先アセンブリが現在の作業ディレクトリ \(コンパイラを起動したディレクトリ\) または共通言語ランタイムのシステム ディレクトリに存在しない場合に、コンパイラが探すディレクトリ。  
  
 `dir2`  
 アセンブリ参照を検索するための 1 つ以上の別のディレクトリ。  ディレクトリ名を複数追加する場合は、空白ではなくコンマで区切って指定します。  
  
## 解説  
 コンパイラは、完全には修飾されていないアセンブリ参照を次の順序で検索します。  
  
1.  現在の作業ディレクトリ。  これは、コンパイラが起動されるディレクトリです。  
  
2.  共通言語ランタイムのシステム ディレクトリ。  
  
3.  **\/lib** で指定したディレクトリ。  
  
4.  LIB 環境変数で指定したディレクトリ。  
  
 アセンブリ参照を指定するには、**\/reference** を使用します。  
  
 **\/lib** は追加して指定できます。繰り返して指定すると前の値に追加されます。  
  
 **\/lib** を使用する代わりに、必須のアセンブリをすべて作業ディレクトリにコピーすることもできます。この場合は、アセンブリ名を **\/reference** に渡すだけです。  その後、作業ディレクトリからアセンブリを削除できます。  依存アセンブリのパスはアセンブリ マニフェストで指定されていないため、アプリケーションをターゲット コンピューターで開始でき、グローバル アセンブリ キャッシュ内のアセンブリを検索および使用できます。  
  
 コンパイラがアセンブリを参照できる場合でも、共通言語ランタイムが実行時にアセンブリを検索して読み込むことができるとは限りません。  実行時に参照アセンブリがどのように検索されるかについては、「[ランタイムがアセンブリを検索する方法](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ ページ\]** ダイアログ ボックスを開きます。  
  
2.  **\[参照パス\]** プロパティ ページをクリックします。  
  
3.  リスト ボックスの内容を変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>」を参照してください。  
  
## 使用例  
 t2.cs をコンパイルして .exe ファイルを作成するには、次のコードを使用します。  コンパイラは、作業ディレクトリと C ドライブのルート ディレクトリでアセンブリ参照を探します。  
  
```  
csc /lib:c:\ /reference:t2.dll t2.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)