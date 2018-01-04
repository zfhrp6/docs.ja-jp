---
title: "x:Type マークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d645d5c953c0ff33435a5648024ace099455e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xtype-markup-extension"></a>x:Type マークアップ拡張機能
CLR の提供<xref:System.Type>指定の XAML 型の基になる型であるオブジェクト。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`prefix`|任意。 既定以外の XAML 名前空間にマップされるプレフィックス。 プレフィックスを指定する多くの場合必要はありません。 「解説」を参照してください。|  
|`typeNameValue`|必須。 現在既定の XAML 名前空間以外に解決可能な型名指定した場合はマップのプレフィックスまたは`prefix`を指定します。|  
  
## <a name="remarks"></a>コメント  
 `x:Type`マークアップ拡張機能と同様の機能は、`typeof()`で演算子[!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)]または`GetType`で演算子[!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]です。  
  
 `x:Type`マークアップ拡張機能は、種類を取得するプロパティの文字列から変換動作を提供<xref:System.Type>です。 入力は、XAML の型です。 入力 XAML の型と CLR の出力間のリレーションシップ<xref:System.Type>出力される<xref:System.Type>は、<xref:System.Xaml.XamlType.UnderlyingType%2A>入力の<xref:System.Xaml.XamlType>、必要なを検索した後<xref:System.Xaml.XamlType>XAML スキーマ コンテキストと、に基づいて<xref:System.Windows.Markup.IXamlTypeResolver>サービス コンテキストを提供します。  
  
 .NET Framework XAML サービスで、このマークアップ拡張機能の処理がによって定義された、<xref:System.Windows.Markup.TypeExtension>クラスです。  
  
 実装では特定のフレームワーク、いくつかのプロパティを受け取る<xref:System.Type>ように、値は、型の名前を直接受け入れることができます (型の文字列値`Name`)。 ただし、この動作を実装することは、複雑なシナリオです。 例については、次の「WPF の使用上の注意」セクションを参照してください。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `x:Type` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 拡張クラスの <xref:System.Windows.Markup.TypeExtension> 値として割り当てられます。 CLR 型に基づいている .NET Framework XAML サービスの既定の XAML スキーマ コンテキスト下でこの属性の値は、いずれか、<xref:System.Reflection.MemberInfo.Name%2A>の目的の型を格納または<xref:System.Reflection.MemberInfo.Name%2A>既定以外の XAML 名前空間のプレフィックスに続くマッピングです。  
  
 `x:Type`オブジェクト要素の構文でマークアップ拡張機能を使用できます。 ここでは、値を指定する、<xref:System.Windows.Markup.TypeExtension.TypeName%2A>プロパティは、拡張機能を正しく初期化するために必要です。  
  
 `x:Type`マークアップ拡張機能は、verbose 属性としても使用できますただしこの使用法は一般的な: `<``object` 。`property``="{x:Type TypeName=``typeNameValue``}" .../>`  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>既定の XAML Namespace と型のマッピング  
 WPF のプログラミングの既定の XAML 名前空間には、通常の XAML シナリオに必要な XAML 型の大部分が含まれていますそのため、XAML 型の値を参照するときに、多くの場合、プレフィックスを回避することができます。 カスタム アセンブリから、または既定の XAML 名前空間にマッピングされませんでした、CLR 名前空間からは、WPF アセンブリ内に存在する型の型を参照している場合、プレフィックスをマップする必要があります。 プレフィックス、XAML 名前空間と CLR 名前空間のマッピングに関する詳細については、次を参照してください。 [XAML 名前空間と WPF XAML 向け Namespace マッピング](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)です。  
  
### <a name="type-properties-that-support-typename-as-string"></a>プロパティをサポート Typename としての文字列を入力します。  
 WPF でサポートされる型の一部のプロパティの値を指定できるようにする手法<xref:System.Type>を必要とせず、`x:Type`マークアップ拡張機能を使用します。 代わりに、型に名前を文字列として値を指定することができます。 この機能にはの例として<xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType>と<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>です。 この動作のサポートは、型コンバーターまたはマークアップ拡張機能のどちらかを通じて提供されていません。 これによって実装され、遅延の動作は、代わりに、<xref:System.Windows.FrameworkElementFactory>です。  
  
 Silverlight は、同様の規則をサポートします。 実際には、Silverlight はサポートされていません`{x:Type}`、XAML 言語のサポートでは受け付けられません`{x:Type}`WPF Silverlight の XAML の移行をサポートするものでは、いくつかの状況の外部で使用します。 したがって、typename-文字列としての動作はすべて Silverlight ネイティブ プロパティの評価に組み込まれている、<xref:System.Type>値です。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 はジェネリック型し、の機能の動作が変更の追加サポートを提供`x:TypeArguments`と`x:Type`このサポートを提供します。  
  
-   `x:TypeArguments`汎用オブジェクトのインスタンス化に関連付けられているオブジェクトの要素がルート以外の要素にあることができます。 詳細については、「XAML 2009」のセクションを参照してください。 [X:typearguments ディレクティブ](../../../docs/framework/xaml-services/x-typearguments-directive.md)です。  
  
-   XAML 2009 では、マークアップでジェネリック型の制約を指定する構文をサポートします。 によって使用されるこの`x:TypeArguments`により、 `x:Type`、または組み合わせで 2 つの機能です。  
  
-   XAML の WPF 実装の負荷では、暗黙の型変換動作の種類を使用する特定のフレームワーク プロパティにこの機能が追加されても、XAML 2009 を処理するときに<xref:System.Type>です。  
  
 WPF では、loose XAML (XAML をマークアップ コンパイルされていない) については、XAML 2009 の機能を使用することができます。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Style>  
 [スタイルとテンプレート](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML の概要 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [マークアップ拡張機能と WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
