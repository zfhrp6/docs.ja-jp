---
title: "TypeConverters および XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b7ee4b3b00a675cfafc884d41079b76656bdf49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="typeconverters-and-xaml"></a>TypeConverters および XAML
このトピックでは、一般的な XAML 言語機能として、文字列からの型変換の目的について説明します。 .NET Framework で、<xref:System.ComponentModel.TypeConverter>クラスは、特定の目的を XAML 属性の使用方法のプロパティ値として使用できる管理対象のカスタム クラスの実装の一部として機能します。 場合は、カスタム クラスを記述する、XAML 設定可能な属性値として使用できるようにするのには、クラスのインスタンスは、適用する必要があります、 <xref:System.ComponentModel.TypeConverterAttribute> 、クラスに記述するカスタム<xref:System.ComponentModel.TypeConverter>クラス、またはその両方です。  
  

  
## <a name="type-conversion-concepts"></a>型変換の概念  
  
### <a name="xaml-and-string-values"></a>XAML と文字列値  
 XAML ファイルで属性値を設定する場合は、その値の最初の型では、文字列が純粋なテキストです。 など、他のプリミティブ<xref:System.Double>最初は、XAML プロセッサに対してテキスト文字列です。  
  
 XAML プロセッサでは、属性値を処理するために 2 つの情報が必要です。 第 1 の情報は、設定しようとしているプロパティの値の型です。 属性値を定義するすべての文字列は、XAML で処理され、最終的にはその型の値に変換 (解決) される必要があります。 値が、XAML パーサーで認識できるプリミティブ (数値など) である場合は、文字列の直接的な変換が試みられます。 値は、列挙体は、その列挙体の名前付き定数に一致する名前を確認する文字列が使用されます。 値がないパーサーで認識されるプリミティブも、列挙型、該当するタイプの場合は、型、または変換後の文字列に基づいて、値のインスタンスを提供できる必要があります。 これは、型コンバーター クラスを示すことによって行います。 型コンバーターは、事実上、コードが .NET コードの呼び出しを別のクラスの XAML シナリオやも可能性がある値を提供するためのヘルパー クラスです。  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>XAML で既存の型変換動作を使用してください。  
 XAML の基礎概念に関する知識、に応じてする可能性があるで既に使用して型変換動作基本的なアプリケーションの XAML 気付かないうちにします。 WPF が文字どおり数百台の型の値を使用するプロパティを定義するインスタンスの<xref:System.Windows.Point>します。 A <xref:System.Windows.Point> 2 次元の座標空間内の座標を記述する値は、次の 2 つの重要なプロパティが実際には:<xref:System.Windows.Point.X%2A>と<xref:System.Windows.Point.Y%2A>です。 XAML 内のポイントを指定する場合として指定する string 区切り記号 (コンマ) との間、<xref:System.Windows.Point.X%2A>と<xref:System.Windows.Point.Y%2A>に指定する値。 たとえば、`<LinearGradientBrush StartPoint="0,0" EndPoint="1,1">` のように指定します。  
  
 この単純型のでも<xref:System.Windows.Point>XAML における単純な使用法が型コンバーターを必要とします。 ここでは、クラス<xref:System.Windows.PointConverter>です。  
  
 型コンバーター<xref:System.Windows.Point>マークアップの使用のすべてのプロパティをクラス レベルの効率化で定義されている<xref:System.Windows.Point>です。 型コンバーター、せずが必要になります次ずっと詳細なマークアップ前に示した例。  
  
 `<LinearGradientBrush>`  
  
 `<LinearGradientBrush.StartPoint>`  
  
 `<Point X="0" Y="0"/>`  
  
 `</LinearGradientBrush.StartPoint>`  
  
 `<LinearGradientBrush.EndPoint>`  
  
 `<Point X="1" Y="1"/>`  
  
 `</LinearGradientBrush.EndPoint>`  
  
 `<LinearGradientBrush>`  
  
 文字列型変換または同等の構文をさらに詳細を使用するかどうかは、一般に、コーディング スタイル選択です。 XAML ツールのワークフローが値の設定方法に影響を与える可能性があります。 一部の XAML ツールは、デザイナー ビューまたは独自のシリアル化メカニズムへのラウンド トリップを簡単になっているために、最も詳細形式のマークアップを生成する傾向があります。  
  
 既存の型コンバーターは通常、クラス (またはプロパティ) を適用の有無をチェック WPF と .NET Framework の型で検出された<xref:System.ComponentModel.TypeConverterAttribute>です。 この属性はその型は、XAML の目的でだけでなく可能性のあるその他の目的の値がサポートする型コンバーターは、クラスに名前を付けます。  
  
### <a name="type-converters-and-markup-extensions"></a>型コンバーターとマークアップ拡張機能  
 マークアップ拡張機能と型コンバーターは、XAML プロセッサの動作とそれらに適用されます、シナリオの観点から両方の役割を入力します。 マークアップ拡張機能の使用時にはコンテキストを利用できますが、マークアップ拡張機能が値を提供するプロパティの型変換動作は一般にマークアップ拡張機能の実装ではチェックされません。 つまり、マークアップ拡張機能としてテキスト文字列を返す場合でもその`ProvideValue`出力は、特定のプロパティまたはプロパティ値の型に適用されると、その文字列に対する型変換動作は呼び出されずに、一般に、マークアップ拡張機能の目的は、プロセスに、文字列と関連する型コンバーターを呼び出さず、オブジェクトを返します。  
  
 ここで、マークアップ拡張機能は、型コンバーターではなく必要な 1 つの一般的な状況を既に存在するオブジェクトへの参照を行います。 最高でステートレスな型コンバーターは、必要とは限らないの新しいインスタンスを生成だけでした。 マークアップ拡張機能の詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
### <a name="native-type-converters"></a>ネイティブな型コンバーター  
 XAML パーサーの WPF と .NET Framework の実装では、を持つネイティブ型の変換処理が通常と考えるのプリミティブ型がまだ特定の種類があります。 このような型の例として、 <xref:System.DateTime>が挙げられます。 この理由は、.NET Framework のアーキテクチャの動作方法に基づいて: 型<xref:System.DateTime>mscorlib、.NET の最も基本的なライブラリで定義されています。 <xref:System.DateTime>依存関係を導入する別のアセンブリから来る属性を持つ属性が設定されることはできません (<xref:System.ComponentModel.TypeConverterAttribute>は System から) ため、属性による通常の型コンバーターの検出機構がサポートされることはできません。 代わりに、XAML パーサーでは、このようなネイティブの処理が必要な型のリストを持つし、通常のプリミティブの処理方法と同様にこれらを処理します。 (の場合、<xref:System.DateTime>への呼び出しでは、この<xref:System.DateTime.Parse%2A>)。  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>型コンバーターの実装  
  
### <a name="typeconverter"></a>TypeConverter  
 <xref:System.Windows.Point>以前は、クラスの例<xref:System.Windows.PointConverter>述べたです。 XAML の目的で使用されるすべての型コンバーターは、基本クラスから派生するクラスを XAML の実装は .NET、<xref:System.ComponentModel.TypeConverter>です。 <xref:System.ComponentModel.TypeConverter> XAML の存在を前にある .NET Framework のバージョンに存在していたクラスです。 ビジュアル デザイナーでのプロパティ ダイアログ ボックスの文字列の変換を提供するが、元の使用法のいずれか。 Xaml での役割<xref:System.ComponentModel.TypeConverter>を展開すると、文字列の属性値を解析およびの文字列に戻す可能性のある特定のオブジェクト プロパティのランタイム値を処理できるようにする文字列に変換して、文字列からの変換の基底クラスが含まれます属性としてシリアル化します。  
  
 <xref:System.ComponentModel.TypeConverter>XAML の処理のための文字列との間の変換に関連する 4 つのメンバーを定義します。  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 これらの最も重要なメソッドは<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>します。 このメソッドは、入力文字列を必要なオブジェクトの種類に変換します。 厳密に言うと、<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>くらい広範な型をコンバーターの目的の型に変換し、そのため、実行時の変換をサポートするなど、XAML の目的で XAML 以外の目的に使用するメソッドを実装する可能性があります処理できるコード パスのみが、<xref:System.String>自分にとって重要な入力です。  
  
 次の重要なメソッドは<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>します。 かどうか、アプリケーションがマークアップ表現に変換されます (たとえば、ファイルとしての XAML に保存される) 場合、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>マークアップ形式を生成を担当します。 この場合、XAML にとって重要なコード パスは、渡す際に、`destinationType`の<xref:System.String>します。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> と <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> は、サービスが <xref:System.ComponentModel.TypeConverter> の実装の機能を照会する時に使用されるサポート メソッドです。 これらのメソッドは、その型について、相当する変換メソッドをコンバーターがサポートしている場合に `true` を返すように実装する必要があります。 XAML の目的では、通常、 <xref:System.String> 型であることを意味します。  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>カルチャ情報と XAML の型コンバーター  
 各<xref:System.ComponentModel.TypeConverter>実装、変換に対して有効な文字列の構成内容の独自の解釈およびことができますも使用したり、パラメーターとして渡される型の説明を無視します。 カルチャと XAML 型の変換に関して重要な考慮事項があります。 XAML では、ローカライズ可能な文字列属性値として使用することはサポートされて完全。 XAML 属性の値の型コンバーターには、必ずしも特定の言語の解析動作が含まれまるために、特定のカルチャ要件を持つ型コンバーターの入力がサポートされていないのでそのローカライズ可能な文字列を使用が、`en-US`カルチャ。 この制限の設計上の理由の詳細については、XAML 言語仕様を参照してください ([\[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525))。  
  
 例として、カルチャが問題になることができます、一部のカルチャが数値の小数点区切り文字としてコンマを使用します。 これが、動作を持つ XAML の WPF 型コンバーターの多くはコンマを区切り記号として使用すると衝突する (共通の X などの従来の慣習に基づき、Y フォーム、またはコンマ区切りリスト)。 周囲の XAML でカルチャを渡すことも (設定`Language`または`xml:lang`を`sl-SI`カルチャ、この方法で小数点のコンマを使用するカルチャの例)、問題は解決しません。  
  
### <a name="implementing-convertfrom"></a>ConvertFrom の実装  
 XAML をサポートする <xref:System.ComponentModel.TypeConverter> の実装としてコンバーターを使用できるようにするためには、そのコンバーターの <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> メソッドが `value` パラメーターとして文字列を受け入れる必要があります。 とき、文字列が有効な書式設定、およびによって変換できる、<xref:System.ComponentModel.TypeConverter>実装し、返されたオブジェクトはプロパティによって予期される型へのキャストをサポートする必要があります。 それ以外の場合、 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 実装は `null`を返す必要があります。  
  
 各<xref:System.ComponentModel.TypeConverter>実装、変換に対して有効な文字列の構成内容の独自の解釈およびことができますも使用したり、パラメーターとして渡された型の説明やカルチャ コンテキストを無視します。 ただし、WPF による XAML 処理の場合は、型の説明コンテキストに値を渡さない場合がありに基づくカルチャを渡さない場合がありますも`xml:lang`します。  
  
> [!NOTE]
>  特に、中かっこ文字を使用しない {、文字列の書式の要素として。 これらの文字は、マークアップ拡張シーケンスの開始および終了を示す文字として予約されています。  
  
### <a name="implementing-convertto"></a>ConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> は、シリアル化のサポートで使用される可能性があります。 カスタム型およびその型コンバーターに対して <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> によるシリアル化をサポートすることは、絶対要件ではありません。 ただし、コントロールを実装する場合、またはクラスの機能または設計の一部としてシリアル化を使用する場合は、 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>を実装する必要があります。  
  
 として使用できるように、 <xref:System.ComponentModel.TypeConverter> XAML をサポートする実装、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>としてそのコンバーターのメソッドがサポートされる型 (または値) のインスタンスを受け入れる必要があります、`value`パラメーター。 ときに、`destinationType`パラメーターの型が<xref:System.String>、返されたオブジェクトとしてキャストできる必要があります、<xref:System.String>です。 返される文字列は、 `value`のシリアル化された値を表している必要があります。 理想的には、シリアル化の形式を選択できる必要がありますにその文字列が渡された場合は、同じ値を生成する、<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>情報の大きな損失が発生せず、同じコンバーターの実装です。  
  
 値をシリアル化することはできません、またはコンバーターがシリアル化をサポートしていない場合、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>実装を返す必要があります`null`、ここで例外をスローすることを許可されています。 例外をスローする場合は、一部としてその変換を使用できないことを報告する必要がありますが、<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>実装ように確認する最善の方法<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>最初の例外を回避するのにはサポートされています。  
  
 場合`destinationType`パラメーターの型ではありません<xref:System.String>、独自のコンバーター処理を選択できます。 通常、処理、basemost の基本実装を元に戻すには<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>特定の例外を発生させます。  
  
### <a name="implementing-canconvertto"></a>CanConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> の実装は、 `true` が `destinationType` 型の場合は <xref:System.String>を返し、それ以外の場合は基底の実装に任せる必要があります。  
  
### <a name="implementing-canconvertfrom"></a>CanConvertFrom の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> の実装は、`sourceType` が <xref:System.String> 型の場合は `true` を返し、それ以外の場合は基底の実装に任せる必要があります。  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute の適用  
 カスタム型コンバーターとして使用するために、XAML プロセッサによってカスタム クラスの型コンバーターを適用する必要がある、 [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute>クラス定義にします。 属性を通して指定する <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> は、カスタム型コンバーターの型名である必要があります。 この属性を適用するには、XAML プロセッサは、プロパティの型が、カスタムのクラス型で使用されている値を処理するときに、入力文字列と、オブジェクト インスタンスを返します。  
  
 また、プロパティごとに型コンバーターを提供することもできます。 適用する代わりに、 [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute>クラス定義にプロパティの定義に適用 (メイン定義されません、 `get` / `set`内に実装)。 プロパティの型は、カスタム型コンバーターによって処理される型と一致する必要があります。 この属性を適用するには、Xaml では、そのプロパティの値を処理するときに、入力文字列を処理し、オブジェクト インスタンスを返します。 プロパティごとに型コンバーターを提供する手法は、[!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] やその他のライブラリなど、クラス定義を制御することができず、<xref:System.ComponentModel.TypeConverterAttribute> を適用できないライブラリからプロパティの型を使用する場合に特に便利です。  
  
## <a name="see-also"></a>参照  
 <xref:System.ComponentModel.TypeConverter>  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
