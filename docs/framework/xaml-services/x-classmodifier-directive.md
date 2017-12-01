---
title: "x:ClassModifier ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: "22"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 111c4a6ed78a908ae3b171dc9349a3c9b81750de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier ディレクティブ
XAML のコンパイルの動作を変更するときに`x:Class`も用意されています。 部分を作成する代わりに、具体的には、`class`を持つ、`Public`アクセス レベル (既定)、指定された`x:Class`で作成された、`NotPublic`アクセス レベル。 この動作では、生成されたアセンブリでクラスのアクセス レベルに影響します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*NotPublic*|正確な文字列を指定に渡す<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>を使用する分離コードのプログラミング言語によって異なります。 「解説」を参照してください。|  
  
## <a name="dependencies"></a>依存関係  
 [X:class](../../../docs/framework/xaml-services/x-class-directive.md)も、同じ要素に提供される必要があり、その要素はページのルート要素である必要があります。 詳細については、次を参照してください。 [ \[MS-XAML\]セクション 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525)です。  
  
## <a name="remarks"></a>コメント  
 値`x:ClassModifier`.NET Framework XAML サービスの使用方法はプログラミング言語によって異なります。 使用する文字列は、各言語の実装に依存その<xref:System.CodeDom.Compiler.CodeDomProvider>と返しますの意味を定義する型コンバーター<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>と<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>、その言語は大文字小文字を区別するかどうかとします。  
  
-   [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]、指定に渡す文字列<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>は`internal`します。  
  
-   [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)]、指定に渡す文字列<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>は`Friend`します。  
  
-   [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]ターゲットをサポートする XAML をコンパイルするが存在しない; そのため、に渡す値は指定されていません。  
  
 指定することも<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>(`public`で[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]、`Public`で[!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)])。 ただし、を指定する<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>が頻度の低い実行されるため<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>は既に既定の動作です。  
  
 その他の値と同じユーザー コードとアクセス レベルの制限など`private`で[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]は関連しない`x:ClassModifier`XAML では、入れ子になったクラスの参照はサポートされていませんし、そのため、<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>修飾子が同じ効果です。  
  
## <a name="security-notes"></a>セキュリティに関する注意事項  
 アクセス レベルで宣言されている`x:ClassModifier`は、特定のフレームワークとその機能によって解釈される可能性があります。 WPF には、読み込みし、型のインスタンスを作成する機能が含まれています。 ここで`x:ClassModifier`は`internal`パック URI 参照を使用して、WPF リソースからそのクラスが参照されている場合、します。 この場合は、可能性のある他のフレームワークによって実装されるようなその他の結果として使用しない専用に`x:ClassModifier`をすべての可能なインスタンス化をブロックしようとします。  
  
## <a name="see-also"></a>関連項目  
 [x:Class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)  
 [WPF における分離コードと XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x:FieldModifier ディレクティブ](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [セキュリティ (WPF)](../../../docs/framework/wpf/security-wpf.md)  
 [WPF から System.Xaml に移行した型](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
