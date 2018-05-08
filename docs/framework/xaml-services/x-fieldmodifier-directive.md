---
title: x:FieldModifier ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 1c7cb10a8021189aaac0ab8cfe5cc04ff8e67905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier ディレクティブ
XAML のコンパイルの動作を変更してでの名前付きオブジェクトの参照フィールドが定義されているように<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>の代わりにアクセス、<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>既定の動作です。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*Public*|正確な指定した文字列を指定する<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>のために使用される分離コードのプログラミング言語によって異なります。 「解説」を参照してください。|  
  
## <a name="dependencies"></a>依存関係  
 XAML の運用環境で使用する場合`x:FieldModifier`任意の場所では、その XAML の運用環境のルート要素を宣言する必要があります、 [X:class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)です。  
  
## <a name="remarks"></a>コメント  
 `x:FieldModifier` 無効、クラスまたはそのメンバーの一般的なアクセス レベルを宣言するためです。 XAML 処理の動作にのみ関連する XAML の運用環境の一部である特定の XAML オブジェクトが処理され、アプリケーションのオブジェクト グラフに可能性のあるアクセス可能なオブジェクトになります。 既定では、このようなオブジェクトのフィールド参照は厳重に保管され、コントロールのコンシューマーは、オブジェクト グラフを直接変更できなきます。 代わりに、コントロール コンシューマーでは有効なプログラミング モデルなどのレイアウト ルート、子要素のコレクション、専用のパブリック プロパティを取得することによって標準のパターンを使用して、オブジェクト グラフを変更する必要と。  
  
 値、`x:FieldModifier`属性は、プログラミング言語によって異なります、特定のフレームワークでの目的が異なります。 使用する文字列は、各言語の実装に依存その<xref:System.CodeDom.Compiler.CodeDomProvider>と返しますの意味を定義する型コンバーター<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>、その言語は大文字小文字を区別するかどうかとします。  
  
-   C# の場合、指定に渡す文字列<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>は`public`します。  
  
-   Microsoft Visual Basic .net の指定に渡す文字列<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>は`Public`します。  
  
-   [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]XAML のターゲット現在存在しません。 そのため、渡す文字列は未定義です。  
  
 指定することも<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>(`internal` 、C# の場合は、 `Friend` Visual Basic で) が指定する<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>はほとんどありませんので`NotPublic`動作は、既に既定値として。  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> XAML をコンパイルされたアセンブリの外側のコードが XAML で作成された要素へのアクセスを必要があることが頻繁ではないために、既定の動作です。 具体的に設定していない場合、XAML のコンパイルの動作と WPF のセキュリティ アーキテクチャは、public として要素のインスタンスを格納するフィールドを宣言しませんが、`x:FieldModifier`パブリック アクセスを許可します。  
  
 `x:FieldModifier` のみを持つ要素の関係、 [X:name ディレクティブ](../../../docs/framework/xaml-services/x-name-directive.md)その名前は public では後にフィールドを参照に使用されるためです。  
  
 既定では、ルート要素の部分クラスはパブリックです。ただし、することができます、パブリックでないを使用して、 [X:classmodifier ディレクティブ](../../../docs/framework/xaml-services/x-classmodifier-directive.md)です。 [X:classmodifier ディレクティブ](../../../docs/framework/xaml-services/x-classmodifier-directive.md)ルート要素クラスのインスタンスのアクセス レベルにも影響します。 両方を配置できる`x:Name`と`x:FieldModifier`ルートに要素が、これだけのパブリック フィールドのコピーを作成は true。 ルート要素クラスのアクセス レベルも、ルート要素によって制御されます[X:classmodifier ディレクティブ](../../../docs/framework/xaml-services/x-classmodifier-directive.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WPF における XAML とカスタム クラス](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [WPF における分離コードと XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x:Name ディレクティブ](../../../docs/framework/xaml-services/x-name-directive.md)  
 [WPF アプリケーション (WPF) のビルド](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [x:ClassModifier ディレクティブ](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
