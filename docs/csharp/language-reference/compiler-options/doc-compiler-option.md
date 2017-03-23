---
title: "/doc (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "FileProperties.BuildAction"
  - "/doc"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "comments, C# code"
  - "XML documentation [C#], comments in source files"
  - "doc compiler option [C#]"
  - "Visual C#, XML documentation for"
  - "-doc compiler option [C#]"
  - "/doc compiler option [C#]"
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# /doc (C# Compiler Options)
**\/doc** オプションを使用すると、XML ファイル内にドキュメント コメントを含めることができます。  
  
## 構文  
  
```  
/doc:file  
```  
  
## Arguments  
 `file`  
 コンパイルするソース コード ファイル内のコメントが出力される XML 形式の出力ファイル。  
  
## 解説  
 ソース コード ファイルでは、次の項目の前にあるドキュメント コメントを処理して、XML ファイルに追加できます。  
  
-   [クラス](../../../csharp/language-reference/keywords/class.md)、[デリゲート](../../../csharp/language-reference/keywords/delegate.md)、[インターフェイス](../../../csharp/language-reference/keywords/interface.md)などのユーザー定義型  
  
-   フィールド、[イベント](../../../csharp/language-reference/keywords/event.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/using-properties.md)、メソッドなどのメンバー  
  
 Main を含むソース コード ファイルが最初に XML に出力されます。  
  
 生成された .xml ファイルで [IntelliSense](/visual-studio/ide/using-intellisense) 機能を使用するには、サポートするアセンブリの名前と .xml ファイル名を同じにして、そのファイルをアセンブリと同じディレクトリに置いてください。  これで、アセンブリが Visual Studio プロジェクトで参照されると、.xml ファイルも同様に検出されます。  詳細については、「[コード コメントの追加](/visual-studio/ide/supplying-xml-code-comments)」を参照してください。  
  
 [\/target: モジュール](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)を指定して、`file` は \<コンパイルの出力ファイルに含めるアセンブリ マニフェスト ファイルの名前を指定するアセンブリ\>\<またはアセンブリ\> タグが含まれています。  
  
> [!NOTE]
>  \/doc オプションは、すべての入力ファイル \(プロジェクトの設定で行った場合は、そのプロジェクト内のすべてのファイル\) に適用されます。  特定のファイルまたはコードの特定セクションについて、ドキュメントのコメントに関する警告を無効にするには、[\#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) を使用します。  
  
 コードのコメントからドキュメントを生成する方法については、「[ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** タブをクリックします。  
  
3.  **\[XML ドキュメント ファイル\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>」を参照してください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)