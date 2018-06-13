---
title: クエリのサポート
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 5c46ed5ae2fc2cc2275bfa7251fe5f8fa346c1f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517992"
---
# <a name="support-for-queries"></a>クエリのサポート
SQL Workflow Instance Store は、一連の既知のプロパティをストアに記録します。 ユーザーは、これらのプロパティに基づいてインスタンスのクエリを実行できます。 これらの既知のプロパティの一部を次の一覧に示します。  
  
-   **サイトの名前。** サービスが存在する Web サイトの名前。  
  
-   **アプリケーションの相対パス。** Web サイトを基準としたアプリケーションの相対パス。  
  
-   **サービスの相対パスです。** アプリケーションを基準としたサービスの相対パス。  
  
-   **サービスの名前です。** サービスの名前。  
  
-   **Service Namespace です。** サービスが使用する名前空間の名称。  
  
-   **現在のコンピューター。**  
  
-   **最後のコンピューター**です。 ワークフロー サービスのインスタンスが最後に実行されたコンピューター。  
  
> [!NOTE]
>  ワークフロー サービス ホストを使用する自己ホスト型のシナリオでは、最後の 4 つのプロパティにのみ値が指定されます。 ワークフロー アプリケーション シナリオでは、最後のプロパティにのみ値が指定されます。  
  
 ワークフロー ランタイムは、最初の 3 つのプロパティの値を指定します。 ワークフロー サービス ホストの値を提供する、**中断の理由**プロパティです。 SQL Workflow Instance Store 自体の値を提供する、**最後に更新されたコンピューター**プロパティです。  
  
 また、SQL Workflow Instance Store の機能により、永続性データベースで値を格納したり、クエリで使用したりするカスタム プロパティを指定することができます。 カスタムの上位変換の詳細については、次を参照してください。[ストア拡張](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)です。  
  
## <a name="views"></a>ビュー  
 インスタンス ストアには、次のビューがあります。 参照してください[永続性データベース スキーマ](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md)詳細についてはします。  
  
### <a name="the-instances-view"></a>Instances ビュー  
 Instances ビューには、次のフィールドがあります。  
  
1.  **ID**  
  
2.  **PendingTimer**  
  
3.  **CreationTime**  
  
4.  **LastUpdatedTime**  
  
5.  **ServiceDeploymentId**  
  
6.  **SuspensionExceptionName**  
  
7.  **SuspensionReason**  
  
8.  **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>ServiceDeployments ビュー  
 ServiceDeployments ビューには、次のフィールドがあります。  
  
1.  **SiteName**  
  
2.  **RelativeServicePath**  
  
3.  **RelativeApplicationPath**  
  
4.  **サービス名**  
  
5.  **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>InstancePromotedProperties ビュー  
 InstancePromotedProperties ビューには、次のフィールドがあります。 昇格させたプロパティの詳細については、「、[ストア拡張](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)トピックです。  
  
1.  **instanceId**  
  
2.  **EncodingOption**  
  
3.  **PromotionName**  
  
4.  **Value #** (からのフィールドの範囲**Value1**に**Value64**)。
