---
title: "カスタム永続参加要素を作成する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c690a0233a425a706ead7441447f589d8330bc0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-custom-persistence-participant"></a>カスタム永続参加要素を作成する方法
次の手順では、永続参加要素を作成します。 参照してください、[永続化に参加している](http://go.microsoft.com/fwlink/?LinkID=177735)サンプルと[ストア拡張](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)永続参加要素のサンプルの実装に関するトピック。  
  
1.  <xref:System.Activities.Persistence.PersistenceParticipant> または <xref:System.Activities.Persistence.PersistenceIOParticipant> クラスから派生するクラスを作成します。 PersistenceIOParticipant クラスには、IO 操作に参加できることに加え、PersistenceParticipant クラスと同じ拡張ポイントが備わっています。 次のうち、必要な手順を行います。  
  
2.  <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> メソッドを実装します。 **CollectValues**メソッドが 2 つのディクショナリ パラメーター、読み取り/書き込み値を格納するため、1 つは他の (後でクエリで使用)、書き込み専用の値を格納します。 このメソッドでは、永続参加要素に固有のデータをこれらのディクショナリに設定する必要があります。 各ディクショナリには、値の名前がキーとして格納されているほか、値そのものが <xref:System.Runtime.DurableInstancing.InstanceValue> オブジェクトとして格納されています。  
  
     ReadWriteValues ディクショナリ内の値としてパッケージ化**InstanceValue**オブジェクト。 書き込み専用のディクショナリ内の値としてパッケージ化**InstanceValue** InstanceValueOptions.Optional および InstanceValueOption.WriteOnly セットを持つオブジェクト。 各**InstanceValue**によって提供される、 **CollectValues**すべての永続参加要素の間での実装は名前が一意である必要があります。  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドを実装します。 **MapValues**メソッドは、パラメーターに似ている 2 つのパラメーターを**CollectValues**メソッドは受信します。 収集されたすべての値、 **CollectValues**ステージはこれらのディクショナリ パラメーターを通じて渡されます。 によって追加された新しい値、 **MapValues**ステージは、書き込み専用値に追加されます。  書き込み専用のディクショナリが、インスタンスの値に直接関連付けられていない外部ソースにデータを提供するために使用されます。 実装によって形成されるそれぞれの値、 **MapValues**すべての永続参加要素の間でのメソッドは名前が一意である必要があります。  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドは <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が提供しない機能を提供し、<xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が処理しなかった別の永続参加により提供される、別の値への依存関係が許可されます。  
  
4.  実装、 **PublishValues**メソッドです。 **PublishValues**メソッドは、永続化ストアから読み込まれたすべての値を含むディクショナリを受け取ります。  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  実装、 **BeginOnSave**メソッド、参加要素が永続 IO 参加要素の場合。 このメソッドは保存操作中に呼び出されます。 このメソッドでは、永続化 (保存) しているワークフロー インスタンスに付随する IO を実行する必要があります。  ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。  さらに、PersistenceIOParticipant はトランザクションの一貫性の要件を通知することがあります。この場合、ホストはほかに使用されなければ、永続化のトランザクションを作成します。  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  実装、 **BeginOnLoad**メソッド、参加要素が永続 IO 参加要素の場合。 このメソッドは読み込み操作中に呼び出されます。 このメソッドでは、ワークフロー インスタンスの読み込みに付随する IO を実行する必要があります。 ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。 さらに、PersistenceIOParticipant はトランザクションの一貫性の要件を通知することがあります。この場合、ホストはほかに使用されなければ、永続化のトランザクションを作成します。  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
