---
title: '方法 : アセンブリから型およびメンバーの情報を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fb06555f18c13f87347a5a76e6f4a3060777f02
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744068"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>方法 : アセンブリから型およびメンバーの情報を取得する
<xref:System.Reflection> 名前空間には、アセンブリから情報を取得するための多くのメソッドがあります。 このセクションでは、これらのメソッドの 1 つを実行する例を示します。 詳細については、「[リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)」を参照してください。  
  
 アセンブリから型およびメンバーの情報を取得する例を次に示します。  
  
## <a name="example"></a>例  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>参照  
 [アプリケーション ドメインを使用したプログラミング](./application-domains.md#programming-with-application-domains) [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)
