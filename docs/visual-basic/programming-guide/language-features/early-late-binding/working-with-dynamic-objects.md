---
title: "動的オブジェクト (Visual Basic) の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 366b563764baaa39849356a782ecee264b2ae94f
ms.lasthandoff: 03/13/2017

---
# <a name="working-with-dynamic-objects-visual-basic"></a>動的オブジェクトの使用 (Visual Basic)
動的オブジェクトの他にも、別の方法を提供、`Object`実行時にオブジェクトに遅延バインディングの種類。 動的オブジェクトで定義されている動的インターフェイスを使用して実行時にプロパティとメソッドのなどのメンバーを公開する、<xref:System.Dynamic>名前空間</xref:System.Dynamic>。 内のクラスを使用する、<xref:System.Dynamic>名前空間を静的な型または形式が一致しないデータ構造を操作するオブジェクトを作成します</xref:System.Dynamic>。 IronPython および IronRuby などの動的言語で定義されている動的オブジェクトを使用することもできます。 動的オブジェクトを作成したり、動的言語で定義されている動的オブジェクトを使用する方法を示す例については、次を参照してください[チュートリアル: 動的オブジェクトの作成および使用して](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、 <xref:System.Dynamic.DynamicObject>、または<xref:System.Dynamic.ExpandoObject>.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject> 。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使用して、動的言語ランタイムと IronPython および IronRuby などの動的言語のオブジェクトにバインド、<xref:System.Dynamic.IDynamicMetaObjectProvider>インターフェイス</xref:System.Dynamic.IDynamicMetaObjectProvider>。 実装するクラスの例として、`IDynamicMetaObjectProvider`インターフェイスは、<xref:System.Dynamic.DynamicObject>と<xref:System.Dynamic.ExpandoObject>クラス</xref:System.Dynamic.ExpandoObject></xref:System.Dynamic.DynamicObject>。  
  
 実装するオブジェクトに遅延バインディング呼び出しを行ったかどうか、`IDynamicMetaObjectProvider`インターフェイス、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]そのインターフェイスを使用して、オブジェクトを動的にオブジェクトにバインドします。 遅延バインディング呼び出しが実装されていないオブジェクトに加えられた場合、`IDynamicMetaObjectProvider`インターフェイス、またはへの呼び出し、`IDynamicMetaObjectProvider`インターフェイスの失敗した場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]オブジェクトの遅延バインディングの機能を使用して、バインド、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ランタイム。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Dynamic.DynamicObject></xref:System.Dynamic.DynamicObject>   
 <xref:System.Dynamic.ExpandoObject></xref:System.Dynamic.ExpandoObject>   
 [チュートリアル: 作成と動的オブジェクトの使用](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)   
 [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
