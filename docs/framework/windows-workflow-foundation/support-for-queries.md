---
title: "クエリのサポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# クエリのサポート
SQL Workflow Instance Store は、一連の既知のプロパティをストアに記録します。ユーザーは、これらのプロパティに基づいてインスタンスのクエリを実行できます。これらの既知のプロパティの一部を次の一覧に示します。  
  
-   **サイト名:** サービスが存在する Web サイトの名前。  
  
-   **相対アプリケーション パス:** Web サイトを基準としたアプリケーションの相対パス。  
  
-   **相対サービス パス:** アプリケーションを基準としたサービスの相対パス。  
  
-   **サービス名:** サービスの名前。  
  
-   **サービスの名前空間:** サービスが使用する名前空間の名称。  
  
-   **現在のコンピューター:**  
  
-   **最後のコンピューター:** ワークフロー サービスのインスタンスが最後に実行されたコンピューター。  
  
> [!NOTE]
>  ワークフロー サービス ホストを使用する自己ホスト型のシナリオでは、最後の 4 つのプロパティにのみ値が指定されます。ワークフロー アプリケーション シナリオでは、最後のプロパティにのみ値が指定されます。  
  
 ワークフロー ランタイムは、最初の 3 つのプロパティの値を指定します。ワークフロー サービス ホストは、**中断の理由**プロパティの値を指定します。SQL Workflow Instance Store 自体は、**最後に更新されたコンピューター** プロパティの値を指定します。  
  
 また、SQL Workflow Instance Store の機能により、永続性データベースで値を格納したり、クエリで使用したりするカスタム プロパティを指定することができます。カスタムの昇格の詳細については、「[ストア拡張](../../../docs/framework/windows-workflow-foundation//store-extensibility.md)」を参照してください。  
  
## ビュー  
 インスタンス ストアには、次のビューがあります。詳細については、「[永続性データベース スキーマ](../../../docs/framework/windows-workflow-foundation//persistence-database-schema.md)」を参照してください。  
  
### Instances ビュー  
 Instances ビューには、次のフィールドがあります。  
  
1.  **Id**  
  
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
  
### ServiceDeployments ビュー  
 ServiceDeployments ビューには、次のフィールドがあります。  
  
1.  **SiteName**  
  
2.  **RelativeServicePath**  
  
3.  **RelativeApplicationPath**  
  
4.  **ServiceName**  
  
5.  **ServiceNamespace**  
  
### InstancePromotedProperties ビュー  
 InstancePromotedProperties ビューには、次のフィールドがあります。昇格されたプロパティの詳細については、「[ストア拡張](../../../docs/framework/windows-workflow-foundation//store-extensibility.md)」を参照してください。  
  
1.  **InstanceId**  
  
2.  **EncodingOption**  
  
3.  **PromotionName**  
  
4.  **Value\#** \(**Value1** から **Value64** までのフィールド範囲\)