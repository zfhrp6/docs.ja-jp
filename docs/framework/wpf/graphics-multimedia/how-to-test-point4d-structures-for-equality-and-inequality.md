---
title: "方法 : Point4D 構造体が等価かどうかをテストする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac69ec232485ebd3097f2db3b31d3fd43d0ccc99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a>方法 : Point4D 構造体が等価かどうかをテストする
この例をテストする方法を示しています。<xref:System.Windows.Media.Media3D.Point4D>等値演算子および非等値の構造体。  
  
 次のコードをテストする方法を示しています。<xref:System.Windows.Media.Media3D.Point4D>構造の等値演算子および非等値を使用して、<xref:System.Windows.Media.Media3D.Point4D>等しいかどうかの方法です。  <xref:System.Windows.Media.Media3D.Point4D>構造があるオーバー ロードされた等しいかどうかを使用する等値テスト (`==`) 演算子をオーバー ロードされた非等値を使用して非等値を (`!=`) 演算子、および最後に、<xref:System.Windows.Media.Media3D.Point3D>構造と<xref:System.Windows.Media.Media3D.Point4D>使用して、静的等値の構造がチェックされます<xref:System.Windows.Media.Media3D.Point4D.Equals%2A>メソッドです。  
  
## <a name="example"></a>例  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
