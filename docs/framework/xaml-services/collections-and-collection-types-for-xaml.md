---
title: "Collections and Collection Types for XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
caps.latest.revision: 2
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 2
---
# Collections and Collection Types for XAML
このトピックではコレクションをサポートするように定義する必要のある親オブジェクトのプロパティ要素または要素の子要素としてコレクション項目のインスタンスを作成するための XAML 構文を説明します。型のプロパティをサポートする方法を示します。  
  
## XAML のコレクションの概念  
 概念的には複数の子項目が XAML オブジェクト要素または XAML プロパティ要素のスコープ内にある XAML のリレーションシップがコレクションとして実装する必要があります。  このコレクションはリレーションシップの親である XAML 型の特定の XAML プロパティに関連付ける必要があります。  プロパティはXAML プロセッサに対応するコレクション プロパティの新しく追加された項目にマークアップの各項目を割り当てる受け取るためコレクションである必要があります。  
  
 XAML 言語レベルでコレクションのサポートの必要条件が完全には定義されていません。  コレクションが一覧になるかまたはディクショナリ \(ただしXAML 言語レベルの両方で\) が定義されているバッキング型を表す概念はXAML 言語にリストまたはディクショナリ定義されません。  
  
 .NET Framework XAML サービスではXAML のコレクションをサポートする概念は.NET Framework のバッキング型の点でより明確に定義されます。  具体的にはコレクションの XAML はリストおよびディクショナリの .NET Framework プログラミングに対して一般的に使用される API と .NET Framework の複数の概念に基づいています。  
  
1.  <xref:System.Collections.IList> インターフェイスはコレクションの一覧を示します。  
  
2.  <xref:System.Collections.IDictionary> のインターフェイスは dicionary コレクションを示しています。  
  
3.  <xref:System.Array> は配列と配列の <xref:System.Collections.IList> のメソッドを表します。  
  
 これらのコレクションの概念にはそれぞれ.NET Framework XAML サービスの XAML プロセッサはコレクション プロパティの型のインスタンスに `Add` のメソッドを呼び出そうとします。  またはシリアル化の場合XAML プロセッサは各コレクションの項目 「」の概念に基づいた辞書リストまたは配列内で検索項目ごとに別個の XAML 型のインスタンスを生成します。  これらは次のとおりです : <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; <xref:System.Array> の明示 <xref:System.Array.System%23Collections%23IList%23Item%2A>。  
  
## ジェネリック コレクション  
 ジェネリック コレクションをプログラミングする通常の場合.NET Framework 便利でありXAML のコレクション プロパティに使用できます。  ただしジェネリック インターフェイス <xref:System.Collections.Generic.IList%601> と <xref:System.Collections.Generic.IDictionary%602> が指定されて <xref:System.Collections.IList> または非ジェネリック <xref:System.Collections.IDictionary> と同等として .NET Framework XAML サービスの XAML プロセッサによって。  インターフェイスを実装するのではなくジェネリック コレクション型のプロパティの推奨される方法はクラス <xref:System.Collections.Generic.List%601> または <xref:System.Collections.Generic.Dictionary%602> から派生させることです。  これらのクラスは非ジェネリック インターフェイスを実装し基本の実装として XAML のコレクションに対して予期されるサポートが含まれます。  
  
## 読み取り専用コレクションと初期化ロジック  
 .NET Framework プログラミングでは読み取り専用コレクションとしてコレクションの値を保持するプロパティを生成する一般的なデザイン パターンです。  このパターンの割り当ての動作を制御するコレクションに改善するためにコレクション プロパティを所有するインスタンス。  具体的にはパターンはプロパティを設定すると既存のコレクションの誤ったを置換します。  このパターンでは呼び出し元によってコレクションに対するアクセスが <xref:System.Collections.IList> などのコレクション型やインターフェイスに関連するコレクションをサポートするように呼び出し元のメソッドやプロパティの代わりにを使用して行う必要があります。  
  
 このパターンを使用して読み取り専用コレクションのプロパティを公開する空のコレクションを保持するクラスは最初にそのプロパティを初期化する必要があります。  通常初期化はクラスのコンストラクターの動作の一部として実行されます。  XAML のプロパティを処理する前に既定のコンストラクターを呼び出すためこのようなロジックは既定のコンストラクターによって常に参照するよう XAML に役立つことが重要でコレクション プロパティ \(またはそのほか\)。  
  
## XAML 型システムのサポートおよびコレクション  
 XAML の基本メカニズムに解析しコレクション プロパティを設定するかシリアル化.NET Framework XAML サービスで実装される XAML 型システムはXAML のコレクションに関するさまざまな設計できますが含まれています。  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A> はXAML の型が XAML のコレクションをサポートする型によってサポートされている場合は true を返します。  
  
2.  コレクション モード XAML 型のサポート <xref:System.Xaml.XamlType.IsDictionary%2A> と <xref:System.Xaml.XamlType.IsArray%2A> では識別できます。  .NET Framework XAML サービスおよびその XAML 型システムに基づいていますが<xref:System.Xaml.XamlWriter> の実装に基づいていないカスタム XAML プロセッサの場合コレクション モードを使用するかはコレクションの処理を開始するためにメソッドを知る必要がある場合があります。  
  
3.  前のプロパティ値にはXAML 型の <xref:System.Xaml.XamlType.LookupCollectionKind%2A> のオーバーライドにでも影響を受けます。