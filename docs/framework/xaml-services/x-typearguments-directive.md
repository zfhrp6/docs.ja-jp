---
title: x:TypeArguments ディレクティブ
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 94f09bdd3b6ee0b180e30bab0993f0b4e41730ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566861"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments ディレクティブ
パスの制約は、ジェネリック型のコンス トラクターにジェネリック型の引数を入力します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`object`|CLR のジェネリック型によってサポートされる XAML 型のオブジェクト要素の宣言。 場合`object`は既定の XAML 名前空間ではない XAML 型を参照`object`XAML 名前空間を示すためにプレフィックスが必要です、`object`が存在します。|  
|`typeString`|1 つまたは複数の XAML を宣言する文字列は、CLR のジェネリック型の型引数を指定する文字列で名前を入力します。 追加の構文のノートの「解説」を参照してください。|  
  
## <a name="remarks"></a>コメント  
 ほとんどの場合、XAML の型情報の項目として使用される、`typeString`文字列の先頭には、します。 一般的な種類の CLR ジェネリック制約 (たとえば、<xref:System.Int32>と<xref:System.String>) CLR 基底クラス ライブラリから取得します。 これらのライブラリを使用して、フレームワーク固有の標準的なマップの既定の XAML 名前空間ではありません、したがって、XAML の使用方法のプレフィックスのマッピングが必要があります。  
  
 コンマ区切り記号を使用して、1 つ以上の XAML 型名を指定できます。  
  
 ジェネリック制約自体がジェネリック型を使用する場合、入れ子になった制約の型引数はかっこ () で含まれていることができます。  
  
 なおのこの定義`x:TypeArguments`が .NET Framework XAML サービスに固有で CLR バッキングを使用しています。 言語レベルの定義は含まれて[ \[MS-XAML\]セクション 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525)です。  
  
## <a name="usage-examples"></a>使用例  
 これらの例については、次の XAML 名前空間の定義が宣言されていることを想定します。  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>リスト\<文字列 >  
 `<scg:List x:TypeArguments="sys:String" ...>` 新しいインスタンスを作成<xref:System.Collections.Generic.List%601>で、<xref:System.String>引数を入力します。  
  
### <a name="dictionarystringstring"></a>ディクショナリ\<String, String >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` 新しいインスタンスを作成<xref:System.Collections.Generic.Dictionary%602>、2 つ<xref:System.String>引数を入力します。  
  
### <a name="queuekeyvaluepairstringstring"></a>キュー < KeyValuePair\<String, String >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 新しいインスタンスを作成<xref:System.Collections.Generic.Queue%601>の制約を持つ<xref:System.Collections.Generic.KeyValuePair%602>内部制約の型引数を持つ<xref:System.String>と<xref:System.String>です。  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 および WPF の汎用的な XAML の使用  
 XAML 2006 の使用状況、および WPF アプリケーションに使用される XAML では、次の制限が存在して`x:TypeArguments`と一般的な XAML からジェネリック型の使用法。  
  
-   XAML ファイルのルート要素だけでは、ジェネリック型を参照する汎用的な XAML の使用方法をサポートできます。  
  
-   ルート要素は、少なくとも 1 つの型引数を持つジェネリック型にマップする必要があります。 例としては<xref:System.Windows.Navigation.PageFunction%601>します。 ページ関数は、wpf XAML ジェネリックの使用状況のサポートの主なシナリオです。  
  
-   ジェネリックのルート要素の XAML オブジェクト要素は、部分クラスを使用しても宣言しなければなりません`x:Class`です。 これは、ビルド アクションを WPF を定義する場合でも当てはまります。  
  
-   `x:TypeArguments` 入れ子になったジェネリック制約は参照できません。  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 またはなし、WPF 3.0 または 3.5 を WPF XAML 2006 の依存関係  
 XAML 2006 または XAML 2009 のいずれかの .NET Framework XAML サービスでは、WPF に関連する汎用の XAML 使用量に制限が緩和されています。 XAML マークアップ、バッキング型システムとオブジェクト モデルをサポートする任意の位置に汎用オブジェクトの要素をインスタンス化することができます。  
  
 XAML 2009 を使用する場合は、CLR のマッピングではなく基本データ型を共通言語プリミティブの XAML 型を取得する、使用することができます[共通の XAML 言語プリミティブの組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)内の情報項目として、`typeString`です。 たとえば、次を宣言する可能性があります (表示されませんが、プレフィックスのマッピングが x は XAML 2009 の XAML 言語の XAML 名前空間)。  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 WPF では、対象とするときに[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、と共に XAML 2009 の機能を使用する`x:TypeArguments`loose XAML (XAML をマークアップ コンパイルされていない) に対してのみです。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。 必要なマークアップをコンパイルした場合、XAML は、「XAML 2006 および WPF 汎用 XAML の使用」セクションで説明した制限で動作する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [x:Class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)  
 [x:Type マークアップ拡張機能](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [共通の XAML 言語プリミティブの組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [XAML のジェネリック](../../../docs/framework/xaml-services/generics-in-xaml.md)
