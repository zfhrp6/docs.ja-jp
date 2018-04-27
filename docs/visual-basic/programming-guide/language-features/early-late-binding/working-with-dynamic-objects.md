---
title: 動的オブジェクトの使用 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f00c57107da5e6ea428e14964d8fa4a870bc96c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="working-with-dynamic-objects-visual-basic"></a>動的オブジェクトの使用 (Visual Basic)
動的オブジェクト以外の別の方法を提供、`Object`実行時にオブジェクトへの遅延バインディングの種類。 動的オブジェクトで定義されている動的のインターフェイスを使用して実行時にプロパティとメソッドなどのメンバーを公開する、<xref:System.Dynamic>名前空間。 クラスを使用することができます、<xref:System.Dynamic>名前空間を静的な型または形式が一致しないデータ構造を操作するオブジェクトを作成します。 IronPython および IronRuby などの動的な言語で定義されている動的オブジェクトを使用することもできます。 動的オブジェクトを作成したり、動的言語で定義されている動的オブジェクトを使用する方法を示す例については、次を参照してください。[チュートリアル: 動的オブジェクトの作成と使用](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、 <xref:System.Dynamic.DynamicObject>、または<xref:System.Dynamic.ExpandoObject>です。  
  
 Visual Basic のオブジェクトへのバインド、動的言語ランタイムと IronPython および IronRuby などの動的言語を使用して、<xref:System.Dynamic.IDynamicMetaObjectProvider>インターフェイスです。 実装するクラスの例については、`IDynamicMetaObjectProvider`のインターフェイスは、<xref:System.Dynamic.DynamicObject>と<xref:System.Dynamic.ExpandoObject>クラスです。  
  
 実装するオブジェクトを遅延バインディング呼び出しが行われたかどうか、`IDynamicMetaObjectProvider`インターフェイス、そのインターフェイスを使用して動的なオブジェクトを Visual Basic バインドします。 遅延バインディング呼び出しが実装されていないオブジェクトへ行われた場合、`IDynamicMetaObjectProvider`インターフェイス、またはへの呼び出し、`IDynamicMetaObjectProvider`インターフェイスが失敗した場合、Visual Basic は、Visual Basic ランタイムの遅延バインディング機能を使用してオブジェクトにバインドします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [チュートリアル: 動的オブジェクトの作成と使用](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
