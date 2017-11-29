---
title: "x:FactoryMethod ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 0d53db49961c2a75e4547f6b57240cefd2cc17c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod ディレクティブ
XAML プロセッサが、バッキング型の解決後、オブジェクトを初期化するために使用するコンス トラクター以外の方法を指定します。  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML 属性の使用方法、x: 引数なし  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML 属性の使用方法、要素として X:arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`methodname`|XAML プロセッサは、として指定されたインスタンスを初期化するために呼び出すメソッドの文字列のメソッド名`object`です。 「解説」を参照してください。|  
|`oneOrMoreObjectElements`|ファクトリ メソッドのパラメーターを指定するオブジェクトのオブジェクトの要素の 1 つ以上 順序は重要です。ファクトリ メソッドに引数を渡す必要があります、順序を示します。|  
  
## <a name="remarks"></a>コメント  
 場合`methodname`インスタンス メソッドでは、修飾することはできません。  
  
 ファクトリ メソッドと静的メソッドがサポートされます。 場合`methodname`静的メソッドでは、`methodname`として提供される、 *typeName*.*methodName*の組み合わせを*typeName*静的ファクトリ メソッドを定義するクラスの名前します。 *typeName*マップされた xmlns で型を参照している場合のプレフィックスで修飾することができます。 *typeName*とは異なる型を指定できます`typeof(``object``)`です。  
  
 工場出荷時のメソッドは、関連するオブジェクトの要素をサポートする型の宣言されたパブリック メソッドである必要があります。  
  
 工場出荷時のメソッドは、関連するオブジェクトに割り当てることができるインスタンスを返す必要があります。 ファクトリ メソッドにする必要があります null を返すことはありません。  
  
 `x:Arguments`ファクトリ メソッドのシグネチャに最も適しているの原則で動作します。 パラメーターの数を最初に評価に一致します。 パラメーターの数に一致する 1 つ以上の場合は、パラメーターの型がで評価されると最適な組み合わせが決定されます。 評価のこのフェーズの後にあいまいさが残る、XAML プロセッサの動作は未定義です。  
  
 `x:FactoryMethod`要素の使用法がプロパティ要素の使用、一般的な意味で、ディレクティブのマークアップが含まれるオブジェクト要素の型を参照していないためです。 推測要素の使用方法は、属性の使用方法ほど一般的です。 `x:Arguments`と共に使用できます (属性または要素のいずれかの利用率)`x:FactoryMethod`要素の使用方法が、これは具体的には表示されません使用状況のセクションでします。  
  
 `x:FactoryMethod`要素には、その他のすべてのプロパティ要素が前に指定する必要があります、としてはいずれかで始まる必要があります`x:Arguments`も、要素として提供されており、コンテンツ/内部のテキスト/初期化のテキストの前にする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [x:Arguments ディレクティブ](../../../docs/framework/xaml-services/x-arguments-directive.md)
