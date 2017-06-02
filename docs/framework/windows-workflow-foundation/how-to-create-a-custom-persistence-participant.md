---
title: "カスタム永続参加要素を作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# カスタム永続参加要素を作成する方法
次の手順では、永続参加要素を作成します。永続参加要素の実装例については、「[永続への参加](http://go.microsoft.com/fwlink/?LinkID=177735)」のサンプルと「[ストア拡張](../../../docs/framework/windows-workflow-foundation//store-extensibility.md)」を参照してください。  
  
1.  <xref:System.Activities.Persistence.PersistenceParticipant> または <xref:System.Activities.Persistence.PersistenceIOParticipant> クラスから派生するクラスを作成します。PersistenceIOParticipant クラスには、IO 操作に参加できることに加え、PersistenceParticipant クラスと同じ拡張ポイントが備わっています。次のうち、必要な手順を行います。  
  
2.  <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> メソッドを実装します。**CollectValues** メソッドには、2 つのディクショナリ パラメーターがあります。1 つは、読み取り\/書き込み可能な値を格納するパラメーターで、もう 1 つは書き込み専用の値を格納するパラメーターです \(後でクエリで使用します\)。このメソッドでは、永続参加要素に固有のデータをこれらのディクショナリに設定する必要があります。各ディクショナリには、値の名前がキーとして格納されているほか、値そのものが <xref:System.Runtime.DurableInstancing.InstanceValue> オブジェクトとして格納されています。  
  
     readWriteValues ディクショナリの値は、**InstanceValue** オブジェクトとしてパッケージ化されています。書き込み専用のディクショナリの値は、InstanceValueOptions.Optional および InstanceValueOption.WriteOnly セットで **InstanceValue** オブジェクトとしてパッケージ化されています。すべての永続参加要素について **CollectValues** の実装によって形成される各 **InstanceValue** の名前は一意である必要があります。  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
  
    ```  
  
3.  <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドを実装します。**MapValues** メソッドが受け取る 2 つのパラメーターは、**CollectValues** メソッドが受け取るパラメーターと似ています。**CollectValues** の段階で収集されるすべての値は、これらのディクショナリ パラメーターを通じて渡されます。**MapValues** の段階で追加される新しい値は、書き込み専用の値に追加されます。書き込み専用のディクショナリが、直接インスタンスの値に関連付けられていない外部ソースにデータを提供するために使用されます。すべての永続参加要素について **MapValues** メソッドの実装によって形成されるそれぞれの値の名前は一意である必要があります。  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドは <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が提供しない機能を提供し、<xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が処理しなかった別の永続参加により提供される、別の値への依存関係が許可されます。  
  
4.  **PublishValues** メソッドを実装します。**PublishValues** メソッドは、永続ストアから読み込まれた値をすべて含むディクショナリを受け取ります。  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
  
    ```  
  
5.  参加要素が永続 IO 参加要素である場合、**BeginOnSave** メソッドを実装します。このメソッドは保存操作中に呼び出されます。このメソッドでは、永続化 \(保存\) しているワークフロー インスタンスに付随する IO を実行する必要があります。ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。さらに、PersistenceIOParticipant はトランザクションの一貫性の要件を通知することがあります。この場合、ホストはほかに使用されなければ、永続化のトランザクションを作成します。  
  
    ```  
  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  参加要素が永続 IO 参加要素である場合、**BeginOnLoad** メソッドを実装します。このメソッドは読み込み操作中に呼び出されます。このメソッドでは、ワークフロー インスタンスの読み込みに付随する IO を実行する必要があります。ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。さらに、PersistenceIOParticipant はトランザクションの一貫性の要件を通知することがあります。この場合、ホストはほかに使用されなければ、永続化のトランザクションを作成します。  
  
    ```  
  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
  
    ```