---
title: インターセプター (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: f3ff08dd4cd20e7ce226750a386cfddb27731923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363801"
---
# <a name="interceptors-wcf-data-services"></a>インターセプター (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 操作にカスタム ロジックを追加できるように、要求メッセージをインターセプトするアプリケーションを有効にします。 このカスタム ロジックを使用して、受信メッセージ内のデータを検証することができます。 このカスタム ロジックを使用して、クエリ要求の範囲をさらに制限することもできます (カスタム認証ポリシーを要求ごとに挿入するなど)。  
  
 先に取得するには、データ サービスで特別なメソッドを使用します。 これらのメソッドは、メッセージ処理の適切なポイントで [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] によって呼び出されます。 インターセプターは、エンティティ セットごとに定義され、サービス操作のように、インターセプター メソッドは、要求からパラメーターを受け取ることはできません。 HTTP GET 要求を処理するときと呼ばれる、クエリ インターセプター メソッドは、インターセプターのエンティティのインスタンスを設定するかどうかを決定するラムダ式は、クエリ結果によって返される必要がありますを返す必要があります。 この式は、要求された操作をさらに絞り込むためにデータ サービスによって使用されます。 次の例は、クエリ インターセプターの定義の例を示します。  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 詳細については、次を参照してください。[する方法: データ サービス メッセージを傍受](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md)です。  
  
 クエリ以外の操作を処理するときに呼び出される変更インターセプターは、`void` (Visual Basic の場合は `Nothing`) を返す必要があります。 変更インターセプター メソッドは、次の 2 つのパラメーターを受け取る必要があります。  
  
1.  エンティティ セットのエンティティ型との互換性がある型のパラメーター。 データ サービスが変更インターセプターを呼び出すとき、このパラメーターの値には、要求によって送信されたエンティティ情報が反映されます。  
  
2.  型 <xref:System.Data.Services.UpdateOperations> のパラメーター。 データ サービスが変更インターセプターを呼び出すとき、このパラメーターの値には、要求が実行しようとしている操作が反映されます。  
  
 次の例は、変更インターセプターの定義の例を示します。  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 詳細については、次を参照してください。[する方法: データ サービス メッセージを傍受](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md)です。  
  
 先に取得する処理には、次の属性がサポートされます。  
  
 **[QueryInterceptor (** *EnitySetName* **)]**  
 ターゲットのエンティティ セット リソースに対する HTTP GET 要求が受信されると、<xref:System.Data.Services.QueryInterceptorAttribute> 属性が適用されたメソッドが呼び出されます。 これらのメソッドは、常に `Expression<Func<T,bool>>` の形式のラムダ式を返す必要があります。  
  
 **[ChangeInterceptor (** *EnitySetName* **)]**  
 ターゲットのエンティティ セット リソースに対する HTTP GET 以外の HTTP 要求が受信されると、<xref:System.Data.Services.ChangeInterceptorAttribute> 属性が適用されたメソッドが呼び出されます。 これらのメソッドは、常に `void` (Visual Basic の場合は `Nothing`) を返します。  
  
 詳細については、次を参照してください。[する方法: データ サービス メッセージを傍受](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md)です。  
  
## <a name="see-also"></a>関連項目  
 [サービス操作](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
