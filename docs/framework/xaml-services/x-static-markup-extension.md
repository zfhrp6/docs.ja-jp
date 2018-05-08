---
title: x:Static のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 980bf6a1bdb19afd5c8d3c798d31037ab8cd7086
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="xstatic-markup-extension"></a>x:Static のマークアップ拡張機能
定義されているすべての静的な値でコードのエンティティを参照して、 [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– 準拠した方法です。 参照される静的プロパティは、XAML では、プロパティの値を提供する使用できます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`prefix`|任意。 割り当てられた、既定以外の XAML 名前空間を表すプレフィックスです。 `prefix` 明示的に使用量のため表示を既定の XAML 名前空間から静的なプロパティを参照することはほとんどありません。 「解説」を参照してください。|  
|`typeName`|必須。 目的の静的メンバーを定義する型の名前。|  
|`staticMemberName`|必須。 静的な値が必要なメンバー (定数、静的なプロパティ、フィールド、または列挙値) の名前。|  
  
## <a name="remarks"></a>コメント  
 参照されているコード エンティティは、次のいずれかにする必要があります。  
  
-   定数  
  
-   静的プロパティ  
  
-   フィールド  
  
-   列挙値  
  
 非静的プロパティなど、他のコード エンティティを指定すると、XAML がマークアップ コンパイルされる、または XAML の読み込み時解析例外の場合のコンパイル時のエラーです。  
  
 ことができます`x:Static`静的フィールドまたは現在の XAML ドキュメントの既定の XAML 名前空間に含まれていないプロパティへの参照ただし、プレフィックスのマッピングが必要です。 XAML 名前空間は、ほとんどの場合、XAML ドキュメントのルート要素で定義されます。  
  
 既定の XAML スキーマ コンテキストで実行されている場合は、.NET Framework XAML サービスおよびその XAML リーダーと XAML ライターによって静的プロパティの参照操作を実行することができます。 この XAML スキーマ コンテキストでは、CLR のリフレクションを使用して、オブジェクト グラフの構築に必要な静的な値を提供します。 `typeName`を指定するは、実際には、XAML の型名を CLR 型名ではなく、既定の XAML スキーマ コンテキストを使用する場合、または既存のすべての CLR ベースの XAML 実装フレームワークを使用する場合は基本的に同じ名前です。  
  
 不用意に加えた`x:Static`直接プロパティの値の型ではない参照をします。 XAML のマークアップ拡張機能で指定した値のシーケンス処理は呼び出されません追加の値の変換。 これは、true の場合でも、`x:Static`参照は、文字列を作成し、通常のテキスト文字列に基づく属性値の値の変換は、特定のメンバーまたは戻り値の型のメンバー値のいずれかが発生しました。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `x:Static` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.Markup.StaticExtension.Member%2A> 拡張クラスの <xref:System.Windows.Markup.StaticExtension> 値として割り当てられます。  
  
 技術的に可能な他の 2 つの XAML 使用法があります。 ただし、これらの使用方法は一般的ではないためにが不必要に詳細です。  
  
 **オブジェクトの要素の構文:** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName` `" .../>`  
  
 **初期化文字列の明示的なメンバーのプロパティ属性の構文:** `<` `object` `` `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName` `}" .../>`  
  
 .NET Framework XAML サービス実装では、このマークアップ拡張機能の処理がによって定義された、<xref:System.Windows.Markup.StaticExtension>クラスです。  
  
 `x:Static` はマークアップ拡張機能です。 XAML の使用中のすべてのマークアップ拡張機能、`{`と`}`マークアップ拡張機能が値を指定する必要がありますを XAML プロセッサが認識する規則は、それぞれの属性構文内の文字です。 マークアップ拡張機能について詳しくは、「 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)」をご覧ください。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 WPF のプログラミングで使用する既定の XAML 名前空間に多数の便利な静的プロパティが含まれていないと、便利な静的プロパティのほとんどを必要とせず、使用状況を容易にする型コンバーターなどのサポートがある`{x:Static}`です。 静的プロパティは、次のいずれかが true の場合、XAML 名前空間のプレフィックスをマップする必要があります。  
  
-   WPF では存在しますが、WPF の既定の XAML 名前空間の一部ではない型を参照している ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)])。 これは、非常に一般的なシナリオを使用するため`x:Static`です。 たとえば、使用する場合があります、`x:Static`に XAML 名前空間のマッピングを持つ参照、 <xref:System> CLR 名前空間と mscorlib のアセンブリの静的プロパティを参照するために、<xref:System.Environment>クラスです。  
  
-   カスタム アセンブリから型を参照しています。  
  
-   その型が WPF 既定の XAML 名前空間の一部であるにマッピングされませんでした、CLR 名前空間内では、WPF アセンブリに存在する型を参照しています。 WPF の既定の XAML 名前空間への CLR 名前空間のマッピングは、さまざまな WPF アセンブリ内の定義によって実行 (この概念の詳細については、次を参照してください。 [XAML 名前空間と WPF XAML 向け Namespace マッピング](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md))。 CLR 名前空間の非対応付けが通常ものではありません、xaml などのクラス定義のほとんどの場合、その CLR 名前空間が構成される場合に存在できる<xref:System.Windows.Threading>です。  
  
 WPF のプレフィックスと XAML 名前空間を使用する方法の詳細については、次を参照してください。 [XAML 名前空間と WPF XAML のマッピングの Namespace](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)です。  
  
## <a name="see-also"></a>関連項目  
 [x:Type マークアップ拡張機能](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [WPF から System.Xaml に移行した型](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
