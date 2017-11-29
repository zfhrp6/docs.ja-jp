---
title: LINQ to DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: de0f11149c2ec587372b9e25f39f35f8552503c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] は、<xref:System.Data.DataSet> オブジェクトにキャッシュされたデータに対するクエリをより簡単に、より高速にします。 具体的には、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]を個別のクエリ言語を使用して、クエリの代わりにプログラミング言語そのものを記述する開発者を有効にしてクエリを簡素化します。 これは特に役立ちます[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]利用できるようのコンパイル時の構文チェック、静的な型指定、IntelliSense のサポートによって提供される、開発者、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]がクエリでします。  
  
 また、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使用すると、1 つまたは複数のデータ ソースから取得して統合したデータを照会することもできます。 これにより、ローカルに集計されたデータのクエリや Web アプリケーションでの中間層のキャッシュなど、データの表現方法や扱いに柔軟性が要求されるさまざまなシナリオが実現します。 特に、汎用のレポート作成、分析、ビジネス インテリジェンスを行うアプリケーションでは、この手法を用いたデータ操作が欠かせません。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]機能は、拡張メソッドによって、主に、公開、<xref:System.Data.DataRowExtensions>と<xref:System.Data.DataTableExtensions>クラスです。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]上に構築し、は、既存[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]アーキテクチャを置き換えるものでありません[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]アプリケーション コードでします。 既存の ADO.NET 2.0 コードは [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] アプリケーションにおいても機能します。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] と [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] のリレーションシップとデータ ストアを次の図に示します。  
  
 ![LINQ to DataSet は、ADO.NET プロバイダーに基づいて](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [プログラミング ガイド](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>参照  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>関連項目  
 [統合言語クエリ (LINQ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ と ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)
