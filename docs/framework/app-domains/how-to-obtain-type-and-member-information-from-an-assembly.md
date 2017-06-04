---
title: "方法 : アセンブリから型およびメンバーの情報を取得する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ [.NET Framework], 取得 (情報を)"
  - "取得 (アセンブリ情報を)"
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : アセンブリから型およびメンバーの情報を取得する
<xref:System.Reflection> 名前空間には、アセンブリから情報を取得するための多くのメソッドがあります。  このセクションでは、これらのメソッドの 1 つを実行する例を示します。  詳細については、「[リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)」を参照してください。  
  
 アセンブリから型情報とメンバー情報を取得する例を次に示します。  
  
## 使用例  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## 参照  
 [Hosting Overview](http://msdn.microsoft.com/ja-jp/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/ja-jp/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)   
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)