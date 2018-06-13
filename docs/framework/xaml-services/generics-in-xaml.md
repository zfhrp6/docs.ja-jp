---
title: XAML のジェネリック
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: faef74c57ac5ff9e3d4162accfc6552db55715bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563585"
---
# <a name="generics-in-xaml"></a>XAML のジェネリック
System.Xaml に実装されている .NET Framework XAML サービスでは、CLR 型のジェネリック型を使用するためのサポートを提供します。 このサポートには、引数の型としてジェネリックの制約を指定して、適切な呼び出しによって、制約の適用が含まれます。`Add`メソッドのジェネリック コレクションの場合。 このトピックを使用して、XAML でのジェネリック型の参照の側面について説明します。  
  
## <a name="xtypearguments"></a>x: TypeArguments  
 `x:TypeArguments` ディレクティブは、XAML 言語によって定義されます。 ジェネリック型によってバックアップされている XAML 型のメンバーとして使用されているときに`x:TypeArguments`型のバッキング コンス トラクターに、ジェネリック引数を渡すの制約を定義します。 .NET Framework XAML サービスに関連する参照構文の使用`x:TypeArguments`、構文の例を含むを参照してください[X:typearguments ディレクティブ](../../../docs/framework/xaml-services/x-typearguments-directive.md)です。  
  
 `x:TypeArguments`文字列を受け取り、型コンバーター バッキングの場合は通常、属性として XAML の使用方法で宣言されています。  
  
 によって、XAML ノード ストリームで、情報が宣言されている`x:TypeArguments`から取得できる<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>で、`StartObject`ノード ストリーム内の位置。 戻り値<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>の一覧を示します<xref:System.Xaml.XamlType>値。 呼び出して、XAML の型がジェネリック型を表すかどうかの決定ができる<xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>です。  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>ルールおよび XAML におけるジェネリックの構文表記規則  
 XAML では、ジェネリック型表す必要が常にある制約付きジェネリック; として制約のないジェネリックでは、XAML 型システムまたは XAML ノード ストリーム内が存在しないと、XAML マークアップで表されることはできません。 ジェネリック型によって参照されているジェネリック型の入れ子にされた型の制約がある場合に、XAML 属性の構文で参照できます`x:TypeArguments`、場合や、`x:Type`ジェネリック型の CLR 型参照を提供します。 これは、 <xref:System.Xaml.Schema.XamlTypeTypeConverter> .NET Framework XAML サービスによって定義されるクラスです。  
  
 XAML 属性の構文形式で有効になって<xref:System.Xaml.Schema.XamlTypeTypeConverter>典型的な MSIL を変更/角度を使用する CLR の構文規則の名前の型と、ジェネリックの制約の角かっこを代わりに制約コンテナーのかっこを置き換えます。 例については、次を参照してください。 [X:typearguments ディレクティブ](../../../docs/framework/xaml-services/x-typearguments-directive.md)です。  
  
## <a name="generics-and-xaml-2009-features"></a>ジェネリックと XAML 2009 の機能  
 XAML 2009 を使用する場合は、CLR のマッピングではなく基本データ型を共通言語プリミティブの XAML 型を取得する、使用することができます[XAML 2009 の組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)情報アイテムとして`x:TypeArguments`です。 たとえば、次を宣言する可能性があります (表示されませんが、マッピングのプレフィックスが`x`は XAML 2009 の XAML 言語の XAML 名前空間)。  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>WPF およびその他の v3.5 フレームワークでジェネリックのサポート  
 具体的には、WPF を対象とする場合の XAML 2006 の使用状況の[X:class](../../../docs/framework/xaml-services/x-class-directive.md)もと同じ要素に提供される必要があります`x:TypeArguments`、し、その要素は、XAML ドキュメントのルート要素である必要があります。 ルート要素は、少なくとも 1 つの型引数を持つジェネリック型にマップする必要があります。 例としては<xref:System.Windows.Navigation.PageFunction%601>します。  
  
 ジェネリックの使用をサポートするために、考えられる回避策など、ジェネリック型を返すことができるカスタム マークアップ拡張機能の定義、折り返しを提供するクラス定義があるが、ジェネリック型から派生した独自のクラス定義内でジェネリック制約を平坦化します。  
  
 対象とする WPF における[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]、と共に XAML 2009 の機能を使用することができます`x:TypeArguments`、loose XAML (XAML をマークアップ コンパイルされていない) に対してのみです。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  
  
 カスタムの Windows Workflow Foundation ワークフロー[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]汎用的な XAML の使用方法をサポートしていません。  
  
## <a name="see-also"></a>関連項目  
 [x:TypeArguments ディレクティブ](../../../docs/framework/xaml-services/x-typearguments-directive.md)  
 [x:Class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)  
 [共通の XAML 言語プリミティブの組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
