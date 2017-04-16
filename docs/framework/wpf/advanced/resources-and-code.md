---
title: "リソースとコード | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "キー, 使用 (オブジェクトを)"
  - "手続き型コード, アクセス (リソースに)"
  - "手続き型コード, 作成 (リソースを)"
  - "リソース, アクセス (手続き型コードから)"
  - "リソース, 作成 (手続き型コードで)"
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# リソースとコード
ここでは、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 構文ではなくコードを使用して、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のリソースにアクセスする方法またはリソースを作成する方法について説明します。  一般的なリソースの使用方法と [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 構文の観点から見たリソースの詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="accessing"></a>   
## コードからリソースにアクセスする  
 リソースを識別するキーは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で定義されていれば、コードでリソースを要求する際にも特定のリソースの取得に使用されます。  コードからリソースを取得する最も簡単な方法は、アプリケーションのフレームワーク レベルのオブジェクトから <xref:System.Windows.FrameworkElement.FindResource%2A> または <xref:System.Windows.FrameworkElement.TryFindResource%2A> メソッドを呼び出すことです。  これらのメソッドは、要求したキーが見つからなかった場合の動作に違いがあります。  <xref:System.Windows.FrameworkElement.FindResource%2A> では例外が発生し、<xref:System.Windows.FrameworkElement.TryFindResource%2A> では例外は発生しませんが `null` が返されます。  各メソッドは、入力パラメーターとしてリソース キーを受け取り、弱く型指定されたオブジェクトを返します。  通常、リソース キーは文字列ですが、文字列以外を使用することもあります。詳細については、「[オブジェクトをキーとして使用する](#objectaskey)」を参照してください。  通常は、返されたオブジェクトを、リソースの要求時に設定するプロパティで必要な型にキャストします。  コードのリソース解決の検索ロジックは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の動的リソース参照の場合と同じです。  リソースの検索は、呼び出し元の要素から開始され、[論理ツリー](GTMT)内の連続する親要素へと続きます。  その後、必要に応じて、アプリケーション リソース、テーマ、およびシステム リソースへと検索が続きます。  コードによるリソースの要求では、リソース ディクショナリが [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で読み込まれた後に行われた実行時の変更と、リアルタイムのシステム リソースの変更が適切に考慮されます。  
  
 キーによってリソースを検索し、戻り値を使用してプロパティを設定する簡単なコード例を次に示します。これは <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーとして実装されます。  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 リソース参照を割り当てる別のメソッドには、<xref:System.Windows.FrameworkElement.SetResourceReference%2A> があります。  このメソッドは、リソースのキーと、リソース値を割り当てる要素インスタンスに存在する特定の依存関係プロパティの識別子の 2 つのパラメーターを受け取ります。  このメソッドは機能的には前のメソッドと同じですが、戻り値をキャストしなくて済むという利点があります。  
  
 他にも、プログラムによってリソースにアクセスする方法として、ディクショナリとしての <xref:System.Windows.FrameworkElement.Resources%2A> プロパティのコンテンツにアクセスする方法があります。  このプロパティによって格納されたディクショナリにアクセスする方法は、新しいリソースを既存のコレクションに追加する方法、指定したキー名がコレクション既に取得されたかどうかを確認する方法などのその他のディクショナリ\/コレクション操作でもあります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション全体をコードで記述する場合は、コレクション全体もコードで作成して、これにキーを割り当て、完了したコレクションを設定されている要素の <xref:System.Windows.FrameworkElement.Resources%2A> プロパティに割り当てることができます。  これについては、次のセクションを参照してください。  
  
 インデックスとして特定のキーを使用して、特定の <xref:System.Windows.FrameworkElement.Resources%2A> コレクション内にインデックスを設定できますが、この方法でリソースにアクセスした場合は、リソース解決で既定の実行時のルールに従っていないことに注意してください。  その特定のコレクションにのみアクセスしています。  要求したキーで有効なオブジェクトが見つからなかった場合、リソース検索がその範囲を超えてルートまたはアプリケーションを走査することはありません。  ただし、この方法はキーの検索範囲がより限定されるため、場合によっては確実にパフォーマンスが向上します。  リソース ディクショナリを直接操作する方法の詳細については、<xref:System.Windows.ResourceDictionary> クラスを参照してください。  
  
<a name="creating"></a>   
## コードでリソースを作成する  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション全体をコードで作成する場合は、そのアプリケーション内のリソースもコードで作成する必要があります。  これを実現するには、新しい <xref:System.Windows.ResourceDictionary> インスタンスを作成し、<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName> を連続して呼び出すことによりすべてのリソースをディクショナリに追加します。  次に、作成された <xref:System.Windows.ResourceDictionary> を使用して、ページ スコープまたは <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> 内にある要素の <xref:System.Windows.FrameworkElement.Resources%2A> プロパティを設定します。  <xref:System.Windows.ResourceDictionary> は、要素に追加せずにスタンドアロン オブジェクトとして保持することもできます。  ただし、これを行う場合は、ジェネリック ディクショナリの場合と同様に、項目のキーによって内部のリソースにアクセスする必要があります。  要素の `Resources` プロパティに割り当てられていない <xref:System.Windows.ResourceDictionary> は、要素ツリーの一部として存在することはなく、一連の検索で <xref:System.Windows.FrameworkElement.FindResource%2A> および関連メソッドによって使用できるスコープがありません。  
  
<a name="objectaskey"></a>   
## オブジェクトをキーとして使用する  
 通常、リソースを使用する場合、リソースのキーは文字列として設定されます。  ただし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の各種機能の中にはキーを指定する際に意図的に文字列型を使用しないで、このパラメーターにオブジェクトを使用するものもあります。  オブジェクトによってリソースにキーを設定するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのスタイルおよびテーマの適用のサポートを利用します。  スタイルが設定されていないコントロールの既定のスタイルとなるテーマのスタイルには、適用されるコントロールの <xref:System.Type> によってそれぞれキーが設定されます。  型によってキーが設定されると、各コントロール型の既定のインスタンスで機能する信頼できる検索機構が実現され、型はリフレクションによって検索できるようになり、派生型に既定のスタイルが設定されていない場合でも派生クラスのスタイルを設定する際に使用できます。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で定義されたリソースの <xref:System.Type> キーは、[x:Type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)を使用して指定できます。  他にも [ComponentResourceKey マークアップ拡張機能](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md)など、文字列以外のキーの使用で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 機能をサポートする同様の拡張機能があります。  
  
## 参照  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)