---
title: "Enterprise Services と COM+ トランザクションの相互運用性  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0fd0d26-fe86-443b-b208-4d57d39fa4aa
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Enterprise Services と COM+ トランザクションの相互運用性 
<xref:System.Transactions> 名前空間は、この名前空間を使用して作成されたトランザクション オブジェクトと COM\+ によって作成されたトランザクションとの間の相互運用をサポートします。  
  
 新しい <xref:System.Transactions.TransactionScope> インスタンスを作成する際に <xref:System.Transactions.EnterpriseServicesInteropOption> 列挙体を使用すれば、COM\+ との相互運用性のレベルを指定することができます。  
  
 既定では、アプリケーション コードが静的 <xref:System.Transactions.Transaction.Current%2A> プロパティを検査すると、<xref:System.Transactions> は、その他の場合は最新であるトランザクション、または <xref:System.Transactions.Transaction.Current%2A> が **null** であることを指示する <xref:System.Transactions.TransactionScope> オブジェクトを探します。どちらも見つからないと、<xref:System.Transactions> は COM\+ コンテキストに照会してトランザクションを探します。<xref:System.Transactions> は、COM\+ コンテキストからトランザクションが見つかる場合でも、<xref:System.Transactions> にネイティブなトランザクションを優先します。  
  
## 相互運用性のレベル  
 <xref:System.Transactions.EnterpriseServicesInteropOption> 列挙体は、<xref:System.Transactions.EnterpriseServicesInteropOption>、<xref:System.Transactions.EnterpriseServicesInteropOption>、および <xref:System.Transactions.EnterpriseServicesInteropOption> の各相互運用性レベルを定義します。  
  
 <xref:System.Transactions.TransactionScope> クラスは、<xref:System.Transactions.EnterpriseServicesInteropOption> をパラメーターとして受け入れるコンストラクターを提供します。  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption> は、その名前が示すように、<xref:System.EnterpriseServices> コンテキストとトランザクション スコープとの間に相互運用性がないことを意味します。<xref:System.Transactions.EnterpriseServicesInteropOption> で <xref:System.Transactions.TransactionScope> オブジェクトを作成した場合は、その後 <xref:System.Transactions.Transaction.Current%2A> にどのような変更を加えても、その変更が COM\+ コンテキストに反映されることはありません。同様に、COM\+ コンテキスト内のトランザクションに対する変更も <xref:System.Transactions.Transaction.Current%2A> には反映されません。追加の同期が必要ないため、これは <xref:System.Transactions> の最速のモードです。<xref:System.Transactions.EnterpriseServicesInteropOption> は、<xref:System.Transactions.EnterpriseServicesInteropOption> をパラメーターとして受け入れないすべてのコンストラクターで、<xref:System.Transactions.TransactionScope> よって使用される既定値です。  
  
 <xref:System.EnterpriseServices> トランザクションをアンビエント トランザクションと組み合わせる場合は、<xref:System.Transactions.EnterpriseServicesInteropOption> または <xref:System.Transactions.EnterpriseServicesInteropOption> のいずれかを使用する必要があります。これらの値はいずれもコンポーネントのないサービスと呼ばれる機能に依存するため、これらの値を使用する際には Windows XP Service Pack 2 または Windows Server 2003 が稼働している必要があります。  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption> は、<xref:System.Transactions> と <xref:System.EnterpriseServices> のアンビエント トランザクションが常に同じものであることを指定します。結果として、新しい <xref:System.EnterpriseServices> トランザクション コンテキストが作成され、そのコンテキストにとって <xref:System.Transactions.TransactionScope> が最新になるようにするため最新のトランザクションが適用されます。そのため、<xref:System.Transactions.Transaction.Current%2A> のトランザクションは <xref:System.EnterpriseServices.ContextUtil.Transaction%2A> のトランザクションと完全に同期することになります。この値を使用すると、新しい COM\+ コンテキストを作成しなければならない場合があるため、パフォーマンスが低下します。  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption> は次の要件を指定します。  
  
-   <xref:System.Transactions.Transaction.Current%2A> が検査されると、<xref:System.Transactions> は、既定のコンテキスト以外のコンテキストで実行されていることを検出した場合、COM\+ コンテキスト内のトランザクションをサポートする必要があります。既定のコンテキストには、トランザクションを含めることができません。したがって、既定のコンテキストでは、<xref:System.Transactions.EnterpriseServicesInteropOption> を使用した場合でも、<xref:System.Transactions> によって使用されるスレッド ローカル ストレージに格納されているトランザクションが <xref:System.Transactions.Transaction.Current%2A> に対して返されます。  
  
-   新しい <xref:System.Transactions.TransactionScope> オブジェクトが作成され、その作成が既定のコンテキスト以外のコンテキストで行われた場合は、<xref:System.Transactions.TransactionScope> オブジェクトにとって最新であるトランザクションが COM\+ に反映される必要があります。この場合、<xref:System.Transactions.EnterpriseServicesInteropOption> は、新しい COM\+ コンテキストを作成するという点で、<xref:System.Transactions.EnterpriseServicesInteropOption> と同様に動作します。  
  
 さらに、<xref:System.Transactions.EnterpriseServicesInteropOption> と <xref:System.Transactions.EnterpriseServicesInteropOption> の両方で <xref:System.Transactions.Transaction.Current%2A> が設定されると、これらのモードはいずれも、<xref:System.Transactions.Transaction.Current%2A> を直接設定できないことを示します。<xref:System.Transactions.TransactionScope> を作成する以外に <xref:System.Transactions.Transaction.Current%2A> を直接設定しようとすると、<xref:System.InvalidOperationException> が発生します。<xref:System.Transactions.EnterpriseServicesInteropOption> 列挙値には、使用する値を明示的に指定しない新しいトランザクション スコープが継承されます。たとえば、新しい <xref:System.Transactions.TransactionScope> オブジェクトを <xref:System.Transactions.EnterpriseServicesInteropOption> で作成した後、2 番目の <xref:System.Transactions.TransactionScope> オブジェクトを作成した場合 \(ただし、<xref:System.Transactions.EnterpriseServicesInteropOption> 値を指定しない\)、その 2 番目の <xref:System.Transactions.TransactionScope> オブジェクトも <xref:System.Transactions.EnterpriseServicesInteropOption> を持つことになります。  
  
 要約すると、新しいトランザクション スコープを作成するときには次の規則が適用されます。  
  
1.  トランザクションがあるかどうかを調べるため <xref:System.Transactions.Transaction.Current%2A> が検査されます。この検査の結果、次のことが行われます。  
  
    -   スコープがあるかどうかが検査されます。  
  
    -   スコープがある場合は、そのスコープが最初に作成されたときに渡された <xref:System.Transactions.EnterpriseServicesInteropOption> 列挙体の値が検査されます。  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption> 列挙体が <xref:System.Transactions.EnterpriseServicesInteropOption> に設定された場合は、COM\+ トランザクション \(<xref:System.EnterpriseServices> トランザクション\) がマネージ スレッド ローカル ストレージ内の <xref:System.Transactions> トランザクションよりも優先されます。  
  
         値が <xref:System.Transactions.EnterpriseServicesInteropOption> に設定された場合は、マネージ スレッド ローカル ストレージ内の <xref:System.Transactions> トランザクションが優先されます。  
  
         値が <xref:System.Transactions.EnterpriseServicesInteropOption> の場合は、トランザクションは 1 つだけあり、それは COM\+ トランザクションです。  
  
2.  <xref:System.Transactions.TransactionScope> コンストラクターによって渡された <xref:System.Transactions.TransactionScopeOption> 列挙体の値が検査されます。これにより、新しいトランザクションを作成する必要があるかどうかが決定されます。  
  
3.  新しいトランザクションを作成する場合は、<xref:System.Transactions.EnterpriseServicesInteropOption> の値に応じてそれぞれ次のようになります。  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption>:  COM\+ コンテキストに関連付けられたトランザクションが作成されます。  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption>: <xref:System.Transactions> トランザクションが作成されます。  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption>: COM\+ コンテキストがある場合は、トランザクションが作成され、そのコンテキストに関連付けられます。  
  
 次の表は、Enterprise Services \(ES\) コンテキストと、<xref:System.Transactions.EnterpriseServicesInteropOption> 列挙体を使用するトランザクションを必要とするトランザクション スコープを示しています。  
  
|ES コンテキスト|なし|自動|完全|  
|---------------|--------|--------|--------|  
|既定のコンテキスト|既定のコンテキスト|既定のコンテキスト|新しいトランザクション コンテキストの作成|  
|既定以外のコンテキスト|クライアントのコンテキストの保守|新しいトランザクション コンテキストの作成|新しいトランザクション コンテキストの作成|  
  
 次の表は、特定の <xref:System.EnterpriseServices> コンテキストと、<xref:System.Transactions.EnterpriseServicesInteropOption> 列挙体を使用するトランザクションを必要とするトランザクション スコープがあると、アンビエント トランザクションがどうなるかを示しています。  
  
|ES コンテキスト|なし|自動|完全|  
|---------------|--------|--------|--------|  
|既定のコンテキスト|ST|ST|ES|  
|既定以外のコンテキスト|ST|ES|ES|  
  
 注:  
  
-   ST は、スコープのアンビエント トランザクションが <xref:System.Transactions> によって管理され、どの <xref:System.EnterpriseServices> コンテキストのトランザクション \(存在する場合\) にも関連付けられていないことを示します。  
  
-   ES は、スコープのアンビエント トランザクションが <xref:System.EnterpriseServices> コンテキストのトランザクションと同じものであることを示します。