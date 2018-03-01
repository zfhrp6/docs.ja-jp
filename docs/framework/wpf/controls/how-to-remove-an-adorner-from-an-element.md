---
title: "方法 : 要素から装飾を削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 20d17ef43f99f6815334c0acbf7eb2040959751e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>方法 : 要素から装飾を削除する
この例は、プログラムから、指定した特定のガイドを削除する方法を示しています。<xref:System.Windows.UIElement>です。  
  
## <a name="example"></a>例  
 この詳細なコード例では、最初のガイドを削除によって返される装飾の配列に<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>です。  この例の発生時に装飾を取得する、<xref:System.Windows.UIElement>という*myTextBox*です。  呼び出しで、要素が指定されている場合<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>、装飾を持たない`null`が返されます。  このコードは明示的に null 配列をチェックしが、null 配列は比較的一般的である必要なアプリケーションに最適です。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>例  
 この圧縮されたコード例は、機能的には、上記の詳細な例です。 このコードに明示的に確認しません null 配列の場合は、可能であればを<xref:System.NullReferenceException>例外が発生する可能性があります。  このコードが、null 配列はまれである必要なアプリケーションに最適です。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>参照  
 [装飾の概要](../../../../docs/framework/wpf/controls/adorners-overview.md)
