---
title: Attributes1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86fa2556e6b8fb82e31a7d4753354aa2dff627ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="attributes"></a>属性
<xref:System.Attribute?displayProperty=nameWithType>カスタム属性を定義するために使用する基本クラスです。  
  
 属性は、アセンブリ、型、メンバー、およびパラメーターなどのプログラミング要素に追加できる注釈です。 これらは、アセンブリのメタデータには保存され、リフレクション Api を使用して実行時にアクセスできます。 たとえば、フレームワークの定義、 <xref:System.ObsoleteAttribute>、型またはメンバーは廃止されていることを示すために、型またはメンバーに適用できます。  
  
 属性は、属性に関連するその他のデータを伝達する 1 つまたは複数のプロパティを持つことができます。 たとえば、`ObsoleteAttribute`のリリースに関する追加情報を実行できる、型またはメンバーが使用されなくなったと廃止された API を置き換える新しい Api の説明。  
  
 属性が適用されるときに、属性の一部のプロパティを指定する必要があります。 これらと呼ばれるに必要なプロパティまたは必須の引数のため、位置指定のコンス トラクターのパラメーターとして表されます。 たとえば、<xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A>のプロパティ、<xref:System.Diagnostics.ConditionalAttribute>必要なプロパティです。  
  
 プロパティがないとは限りません属性が適用されたときに指定するのには、省略可能なプロパティ (または省略可能な引数) と呼ばれます。 設定可能なプロパティによって表されます。 コンパイラでは、属性が適用されるときに、これらのプロパティを設定する特別な構文を提供します。 たとえば、<xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>プロパティは省略可能な引数を表します。  
  
 **✓ しないで**「属性」サフィックスを持つカスタム属性クラスの名前  
  
 **✓ しないで**適用、<xref:System.AttributeUsageAttribute>カスタム属性にします。  
  
 **✓ しないで**省略可能な引数の設定可能なプロパティを提供します。  
  
 **✓ しないで**必須の引数の取得専用のプロパティを提供します。  
  
 **✓ しないで**必須の引数に対応するプロパティを初期化するコンス トラクターのパラメーターを指定します。 各パラメーターにすることは、同じ名前 (大文字小文字が異なる) には、対応するプロパティです。  
  
 **避け x**省略可能な引数に対応するプロパティを初期化するコンス トラクターのパラメーターを指定します。  
  
 つまり、コンス トラクターと、set アクセス操作子の両方で設定できるプロパティがありません。 このガイドラインは、明示的に指定する引数は省略可能なこれが必要であり、2 つの方法で同じことを行う必要はなくなります。  
  
 **避け x**カスタム属性のコンス トラクターのオーバー ロードします。  
  
 コンス トラクターの 1 つだけのことを明確に伝達をユーザーにどの引数が必須および省略可能な。  
  
 **✓ しないで**可能であれば、カスタム属性クラスをシールします。 これにより、属性の参照も高速です。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
