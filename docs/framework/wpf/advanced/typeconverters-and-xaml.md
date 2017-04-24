---
title: "TypeConverters および XAML | Microsoft Docs"
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
  - "クラス, TypeConverter"
  - "TypeConverter クラス"
  - "XAML, TypeConverter クラス"
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# TypeConverters および XAML
ここでは、XAML 言語の一般的な機能である文字列からの型変換の目的について説明します。  .NET Framework において、<xref:System.ComponentModel.TypeConverter> クラスは、XAML の属性でプロパティ値として使用できるカスタムのマネージ クラスの実装の一部として、特別な役割を果たします。  カスタム クラスを作成し、そのクラスのインスタンスを XAML の設定できる属性値として使用できるようにするには、そのクラスに <xref:System.ComponentModel.TypeConverterAttribute> を適用するか、カスタムの <xref:System.ComponentModel.TypeConverter> クラスを作成するかのいずれか、または両方を行う必要があります。  
  
   
  
## 型変換の概念  
  
### XAML と文字列値  
 XAML ファイルで属性値を設定するとき、その値の初期型はピュア テキストの文字列です。  <xref:System.Double> などの他のプリミティブ型であっても、XAML プロセッサにとっては最初はテキスト文字列です。  
  
 属性値を処理するために、XAML プロセッサは 2 つの情報を必要とします。  第 1 の情報は、設定するプロパティの値型です。  属性値を定義し、XAML で処理される文字列値はすべて、最終的にその型の値に変換 \(解決\) される必要があります。  その値が XAML パーサーで認識されるプリミティブ \(数値など\) である場合は、文字列の直接的な変換が試みられます。  値が列挙体の場合は、文字列を使用して、その列挙体で一致する名前付き定数がチェックされます。  値がパーサーで認識されるプリミティブでも列挙体でもない場合、その値の型は、変換される文字列に基づいて、型のインスタンス \(値\) も提供できるようにする必要があります。  これは、型コンバーター クラスを指定することによって行われます。  型コンバーターは、XAML で使用する場合や、.NET コードでコード呼び出しを行う場合には、実質的に他のクラスの値を生成するためのヘルパー クラスとして機能します。  
  
### XAML における既存の型変換動作の使用  
 XAML の基礎概念に対する開発者の理解度によっては、基本的なアプリケーション XAML で気付かないうちに既に型変換動作を使用している場合もあります。  たとえば、WPF では、<xref:System.Windows.Point> 型の値を格納するプロパティが、文字どおり数百種類も定義されています。  <xref:System.Windows.Point> は、2 次元の座標空間における座標を表す値で、実際に <xref:System.Windows.Point.X%2A> および <xref:System.Windows.Point.Y%2A> という 2 つの重要なプロパティだけが定義されています。  XAML でポイントを指定するときは、指定する <xref:System.Windows.Point.X%2A> 値と <xref:System.Windows.Point.Y%2A> 値の間に区切り文字 \(通常はコンマ\) を挿入した文字列として指定します。  たとえば、`<LinearGradientBrush StartPoint="0,0" EndPoint="1,1">` のように指定します。  
  
 <xref:System.Windows.Point> のように単純な型は、XAML における使用方法も簡単ですが、このような場合でも型コンバーターが使用されます。  この場合、型コンバーターは <xref:System.Windows.PointConverter> クラスです。  
  
 <xref:System.Windows.Point> の型コンバーターはクラス レベルで定義されているため、<xref:System.Windows.Point> を格納するプロパティは、すべて簡単なマークアップ形式で指定できます。  型コンバーターが定義されていない場合、前に示した例では、次のように非常に複雑なマークアップが必要となります。  
  
 `<LinearGradientBrush>`  
  
 `<LinearGradientBrush.StartPoint>`  
  
 `<Point X="0" Y="0"/>`  
  
 `</LinearGradientBrush.StartPoint>`  
  
 `<LinearGradientBrush.EndPoint>`  
  
 `<Point X="1" Y="1"/>`  
  
 `</LinearGradientBrush.EndPoint>`  
  
 `<LinearGradientBrush>`  
  
 型変換文字列と、より複雑な同等の構文のどちらを使用するかは、多くの場合、コーディングのスタイルによって異なります。  また、XAML ツールのワークフローも、値の設定方法に影響する場合があります。  一部の XAML ツールは、非常に複雑な形式のマークアップを作成する傾向があります。これは、デザイナー ビューまたはそのシリアル化メカニズムへのラウンド トリップが簡単なためです。  
  
 WPF 型および .NET Framework 型の既存の型コンバーターの検出は、通常、クラス \(またはプロパティ\) に <xref:System.ComponentModel.TypeConverterAttribute> が適用されているかどうかを調べることによって行われます。  この属性は、XAML やその他の目的で型を使用するときのために、その型の値に対応するサポートされている型コンバーターを表すクラスを指定します。  
  
### 型コンバーターとマークアップ拡張機能  
 マークアップ拡張機能と型コンバーターは、XAML プロセッサの動作とこれらが適用されるシナリオの観点で直交的な役割を果たします。  マークアップ拡張機能の使用時にはコンテキストを利用できますが、マークアップ拡張機能が値を提供するプロパティの型変換動作は一般にマークアップ拡張機能の実装ではチェックされません。  つまり、マークアップ拡張機能が `ProvideValue` 出力としてテキスト文字列を返す場合でも、特定のプロパティまたはプロパティの値型に適用される、対象の文字列に対する型変換動作は呼び出されません。一般に、マークアップ拡張機能の目的は、型コンバーターを呼び出すことなく、文字列を処理し、オブジェクトを返すことです。  
  
 型コンバーターではなくマークアップ拡張機能が必要となる典型的な状況の 1 つとして、既存のオブジェクトへの参照が挙げられます。  状態非依存の型コンバーターは、必要とは限らない新しいインスタンスを生成するだけです。  マークアップ拡張機能の詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
### ネイティブな型コンバーター  
 XAML パーサーの WPF および .NET Framework 実装には、ネイティブな型変換処理を定義しているが、従来ならばプリミティブ型として扱うことができなかった型があります。  このような型の例として、<xref:System.DateTime> が挙げられます。  その理由は、.NET Framework アーキテクチャがどのように機能するかに基づいています。<xref:System.DateTime> 型は、.NET の最も基本的なライブラリである mscorlib で定義されています。  <xref:System.DateTime> の属性は、依存関係を伴う他のアセンブリの属性では指定できないため \(<xref:System.ComponentModel.TypeConverterAttribute> は System の属性\)、属性を使用した通常の型コンバーター検出機構は使用できません。  代わりに、このようなネイティブな処理が必要な型の一覧が XAML パーサーに用意されており、XAML パーサーは、これらの型を通常のプリミティブ型と同様の方法で処理します。  <xref:System.DateTime> の場合、これは <xref:System.DateTime.Parse%2A> への呼び出しに相当します。  
  
<a name="Implementing_a_Type_Converter"></a>   
## 型コンバーターの実装  
  
### TypeConverter  
 前に示した <xref:System.Windows.Point> の例で、<xref:System.Windows.PointConverter> というクラスについて触れました。  XAML の .NET 実装では、XAML で使用されるすべての型コンバーターは、<xref:System.ComponentModel.TypeConverter> 基本クラスからの派生クラスです。  <xref:System.ComponentModel.TypeConverter> クラスは、XAML が登場する前のバージョンの .NET Framework にもありました。このクラスの元来の目的の 1 つは、ビジュアルなデザイナーでプロパティ ダイアログの文字列変換を行うことでした。  XAML では、<xref:System.ComponentModel.TypeConverter> の役割が拡張され、文字列への変換と文字列からの変換のための基本クラスとなりました。これにより、文字列の属性値を解析することや、特定のオブジェクト プロパティの実行時の値を文字列に再変換して、属性としてシリアル化することができるようになっています。  
  
 <xref:System.ComponentModel.TypeConverter> には、XAML の処理を目的とした文字列の変換に関係する、次の 4 つのメンバーが定義されています。  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 これらのうち、最も重要なメソッドは <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> です。  このメソッドは、入力文字列を必要なオブジェクト型に変換します。  厳密に言うと、<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> メソッドは、より多くの型をコンバーターの目的の型に変換するように実装することができるため、XAML 以外の目的 \(実行時の変換に対するサポートなど\) にも使用できます。ただし、XAML では、対象となる <xref:System.String> 入力を処理するためのコード パスにすぎません。  
  
 次に重要なメソッドは <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> です。  アプリケーションをマークアップ表現に変換する場合 \(アプリケーションを XAML にファイルとして保存する場合など\)、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> は、マークアップ表現の生成を行います。  この場合、XAML に関係するコード パスは、<xref:System.String> の `destinationType` を渡すときです。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> と <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> は、<xref:System.ComponentModel.TypeConverter> 実装の機能をサービスが照会するときに使用されるサポート メソッドです。  これらのメソッドは、コンバーターの対応する変換メソッドが、型固有の状況をサポートしている場合に、`true` を返すように実装する必要があります。  XAML では、通常、<xref:System.String> 型について true が返されます。  
  
### カルチャ情報と XAML の型コンバーター  
 各 <xref:System.ComponentModel.TypeConverter> の実装には、変換に有効な文字列の構成内容に関する独自の解釈を含めることができます。また、パラメーターとして渡された型説明を使用したり無視したりすることもできます。  カルチャと XAML の型変換については、重要な考慮事項があります。  XAML では、ローカライズできる文字列を属性値として全面的に使用できます。  ただし、そのローカライズできる文字列を、特定のカルチャ要件と共に型コンバーターの入力として使用することはできません。これは、XAML 属性値の型コンバーターには、必ず特定の言語の解析動作 \(`en-US` カルチャを使用\) が組み込まれているためです。  この制限に関する設計上の理由の詳細については、XAML 言語仕様  \(「[\[MS\-XAML \(MS\-XAML\)\]](http://go.microsoft.com/fwlink/?LinkId=114525)」\) を参照してください。  
  
 カルチャが問題となる例として、一部のカルチャで数値の小数点記号にコンマが使用されていることが挙げられます。  これは、多くの WPF XAML 型コンバーターで定義されているコンマを区切り文字として使用する動作 \(一般的な "X,Y" 形式やコンマ区切りリストなど従来の慣習を基準とした動作\) と重複します。  周囲の XAML でカルチャを指定しても \(`Language` または `xml:lang` を、コンマを小数点記号として使用するカルチャの 1 つである `sl-SI` に設定しても\)、問題は解決しません。  
  
### ConvertFrom の実装  
 XAML をサポートする <xref:System.ComponentModel.TypeConverter> の実装としてコンバーターを使用できるようにするためには、そのコンバーターの <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> メソッドが、`value` パラメーターとして文字列を受け入れる必要があります。  文字列が有効な形式であり、<xref:System.ComponentModel.TypeConverter> 実装で変換できる場合、返されるオブジェクトは、プロパティで予想される型へのキャストをサポートしている必要があります。  それ以外の場合は、<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 実装は `null` を返す必要があります。  
  
 各 <xref:System.ComponentModel.TypeConverter> の実装には、変換に有効な文字列の構成内容に関する独自の解釈を含めることができます。また、パラメーターとして渡された型説明やカルチャ情報を使用したり無視したりすることもできます。  ただし、WPF XAML 処理が、値を型説明コンテキストに渡さない場合があり、`xml:lang` に基づくカルチャを渡さない場合もあります。  
  
> [!NOTE]
>  文字列の書式の要素として、中かっこ文字、特に { は使用しないでください。  これらの文字は、マークアップ拡張シーケンスの開始および終了を示す文字として予約されています。  
  
### ConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> はシリアル化のサポートで使用される場合があります。  <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> を使用したカスタム型およびその型コンバーターのシリアル化のサポートは、絶対要件ではありません。  ただし、コントロールを実装する場合、またはクラスの機能または設計の一部としてシリアル化を使用する場合は、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> を実装する必要があります。  
  
 XAML をサポートする <xref:System.ComponentModel.TypeConverter> の実装としてコンバーターを使用できるようにするためには、そのコンバーターの <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> メソッドが、`value` パラメーターとして、サポートされる型のインスタンス \(または値\) を受け入れる必要があります。  `destinationType` パラメーターが <xref:System.String> 型の場合は、返されるオブジェクトは <xref:System.String> にキャストできる必要があります。  返される文字列は、`value` のシリアル化された値を表す必要があります。  理想的には、選択するシリアル化形式は、その文字列が同じコンバーターの <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> の実装に渡された場合に、情報の大きな損失が発生することなく、同じ値を生成できる必要があります。  
  
 値をシリアル化できない場合、またはコンバーターがシリアル化をサポートしていない場合は、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> の実装は `null` を返す必要があり、この場合に例外をスローすることもできます。  ただし、例外をスローする場合は、<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> の実装の一部として変換を使用できないことを示すことにより、事前に <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> を確認して例外の発生を回避するというベスト プラクティスに対応する必要があります。  
  
 `destinationType` パラメーターが <xref:System.String> 型でない場合は、独自のコンバーターの処理を選択できます。  通常は、基本実装の処理 \(基本の <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> では特定の例外が発生する\) に戻ることになります。  
  
### CanConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> の実装は、`destinationType` が <xref:System.String> 型の場合には `true` を返し、それ以外の場合は基本実装に任せるようにする必要があります。  
  
### CanConvertFrom の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> の実装は、<xref:System.String> 型の `sourceType` に対しては `true` を返し、それ以外の場合は基本実装に任せます。  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## TypeConverterAttribute の適用  
 カスタムの型コンバーターがカスタム クラス用の型コンバーターとして XAML プロセッサで実際に使用されるようにするには、[!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> をクラス定義に適用する必要があります。  属性で指定する <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> は、カスタム型コンバーターの型名である必要があります。  この属性を適用すると、プロパティの型としてカスタム クラス型が使用される場合に、XAML プロセッサが値を処理する際、入力文字列を処理して、オブジェクト インスタンスを返すことができます。  
  
 また、プロパティごとに型コンバーターを提供することもできます。  クラス定義に [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> を適用する代わりに、プロパティ定義 \(メイン定義内の `get`\/`set` 実装ではなくメイン定義自体\) に適用します。  プロパティの型は、カスタム型コンバーターによって処理される型と一致する必要があります。  この属性を適用すると、そのプロパティの値を XAML プロセッサが処理する際に、入力文字列を処理して、オブジェクト インスタンスを返すことができます。  プロパティごとの型コンバーターは、[!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] のプロパティ型を使用する場合、またはクラス定義を制御できず、<xref:System.ComponentModel.TypeConverterAttribute> を適用できない他のライブラリのプロパティ型を使用する場合に、特に役立ちます。  
  
## 参照  
 <xref:System.ComponentModel.TypeConverter>   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)