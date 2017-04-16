---
title: "動的なソース コードの生成とコンパイル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Code Document Object Model"
  - "CodeDOM"
  - "言語に依存しないソース コードのモデル化"
  - "言語, 複数言語のサポート (CodeDOM による)"
  - "複数言語 (CodeDOM によりサポートされる)"
  - "ソース コード (複数言語を使用した)"
  - "System.CodeDom 名前空間"
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 動的なソース コードの生成とコンパイル
.NET Framework には、CodeDOM \(Code Document Object Model\) と呼ばれる機構が用意されています。CodeDOM を使用すると、ソース コードを出力するプログラムの開発者は、レンダリング対象となるコードを表す単一のモデルに基づいて、実行時に複数のプログラミング言語でソース コードを生成するプログラムを開発できます。  
  
 ソース コードを表現するために、CodeDOM 要素が相互にリンクされ、CodeDOM グラフと呼ばれるデータ構造体が形成されます。このデータ構造体は、ソース コードの構造をモデル化します。  
  
 `System.CodeDom` 名前空間は、特定のプログラミング言語に依存せずに、ソース コードの論理構造を表すことができる型を定義します。  `System.CodeDom.Compiler` 名前空間は、CodeDOM グラフからソース コードを生成し、サポートされている言語でソース コードのコンパイルを管理する型を定義します。  コンパイラの販売元および開発者は、サポートされている言語のセットを拡張できます。  
  
 言語に依存しないソース コードのモデル化は、プログラムで複数の言語または不特定の対象言語のプログラム モデルのソース コードを生成する必要がある場合に役立ちます。  たとえば、言語の CodeDOM サポートが利用できる場合は、デザイン時に CodeDOM を言語抽象化インターフェイスとして使用し、適切なプログラミング言語でソース コードを生成できます。  
  
 .NET Framework には、[C\#](frlrfMicrosoftCSharpCSharpCodeProviderClassTopic) 用、[JScript](frlrfMicrosoftJScriptJScriptCodeProviderClassTopic) 用、および [Visual Basic](frlrfMicrosoftVisualBasicVBCodeProviderClassTopic) 用のコード ジェネレーターとコード コンパイラが用意されています。  
  
## このセクションの内容  
 [CodeDOM の使用方法](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 CodeDOM の一般的な使用方法を説明し、CodeDOM を使って簡単なオブジェクト グラフを構築する例を示します。  
  
 [CodeDOM グラフからのソース コードの生成およびプログラムのコンパイル](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 ソース コードを生成する方法と、生成されたコードを `System.CodeDom.Compiler` 名前空間で定義されているクラスを使って外部コンパイラでコンパイルする方法について説明します。  
  
 [方法: CodeDOM を使用して XML ドキュメント ファイルを作成する](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 CodeDOM を使用して XML ドキュメントのコメント付きのコードを生成する方法、および生成されたコードをコンパイルして XML ドキュメント出力を作成する方法について説明します。  
  
 [方法 : CodeDOM を使用してクラスを作成する](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 CodeDOM を使用してフィールド、プロパティ、メソッド、コンストラクター、およびエントリ ポイントを持つクラスを生成する方法を説明します。  
  
## 関連項目  
 <xref:System.CodeDom>  
 共通言語ランタイムを対象とするプログラミング言語のコード要素を表す要素を定義します。  
  
 <xref:System.CodeDom.Compiler>  
 実行時にコードを生成およびコンパイルするためのインターフェイスを定義します。  
  
## 関連項目  
 [CodeDOM Quick Reference](http://msdn.microsoft.com/ja-jp/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 ソース コードの要素を表す CodeDOM 要素を簡単に検索するための方法が用意されています。