---
title: "追跡プロファイル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# 追跡プロファイル
追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信することを可能にする追跡クエリが含まれています。  
  
## 追跡プロファイル  
 追跡プロファイルは、どの追跡情報をワーク フロー インスタンスに出力するか指定するために使用されます。プロファイルが指定されていない場合、すべての追跡イベントが出力されます。プロファイルを指定した場合、プロファイルで指定された追跡イベントが出力されます。監視の要件に応じて、ワークフローの主な状態変化の少数のセットを定期受信する、非常に一般的なプロファイルを作成できます。それとは反対に、結果として得られるイベントが、後で詳細な実行フローを十分に再構築できる極めて詳細なプロファイルを作成することもできます。  
  
 追跡プロファイルは、標準の [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 構成ファイル内の XML 要素や、コードで指定される XML 要素として出現します。追跡参加要素が `Started` と `Completed` のワークフロー イベントを定期受信できるようにする構成ファイルの [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 追跡プロファイルの例を次に示します。  
  
```  
<system.serviceModel>  
    ...  
    <tracking>    
      <trackingProfile name="Sample Tracking Profile">  
        <workflow activityDefinitionId="*">  
          <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                <state name="Started"/>  
                <state name="Completed"/>  
              </states>  
            </workflowInstanceQuery>  
          </workflowInstanceQueries>  
        </workflow>  
      </trackingProfile>          
    </profiles>  
  </tracking>  
    ...  
</system.serviceModel>  
  
```  
  
 次の例では、コードを使用して作成された同等の追跡プロファイルを示します。  
  
```csharp  
TrackingProfile profile = new TrackingProfile()  
{  
    Name = "CustomTrackingProfile",  
    Queries =   
    {  
        new WorkflowInstanceQuery()  
        {  
            // Limit workflow instance tracking records for started and  
            // completed workflow states.  
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },  
        }  
    }  
};  
  
```  
  
 追跡レコードは、<xref:System.Activities.Tracking.ImplementationVisibility> 属性を使用して、追跡プロファイル内部の表示モードを通じてフィルター処理されます。複合アクティビティは、その実装を形成する他のアクティビティを含む最上位アクティビティです。表示モードは、実装を形成するアクティビティが追跡されているかどうかを指定するために、ワークフロー アクティビティ内の複合アクティビティから生成された追跡レコードを指定します。表示モードは、追跡プロファイル レベルで適用されます。ワークフロー内にある個々のアクティビティの追跡レコードのフィルター処理は、追跡プロファイル内のクエリによって制御されます。詳細については、このドキュメントで後述される「**プロファイルのクエリの型の追跡**」を参照してください。  
  
 追跡プロファイルの `implementationVisibility` 属性で指定される 2 つの表示モードは、`RootScope` と `All` です。`RootScope` モードを使用すると、複合アクティビティがワークフローのルート アクティビティでない場合にアクティビティの実装を形成するアクティビティの追跡レコードが抑制されます。したがって、他のアクティビティを使用して実装されているアクティビティがワークフローに追加された場合、`implementationVisibility` が RootScope に設定されていると、その複合アクティビティ内の最上位アクティビティのみが追跡されます。アクティビティがワークフローのルート アクティビティである場合、アクティビティの実装はワークフローそのものであり、追跡レコードはその実装を形成するアクティビティを対象として生成されます。All モードを使用すると、ルート アクティビティとそのすべての複合アクティビティを対象として、すべての追跡レコードを生成できます。  
  
 たとえば、*MyActivity* は *Activity1* と *Activity2* の 2 つのアクティビティが実装に含まれている複合アクティビティである、とします。この複合アクティビティがワークフローに追加され、`implementationVisibility` が `RootScope` に設定された追跡プロファイルで追跡が有効化されると、追跡レコードは *MyActivity* のみを対象として生成されます。しかし、*Activity1* と *Activity2* の各アクティビティについてはレコードは生成されません。  
  
 これに対して、追跡プロファイルの `implementationVisisbility` 属性が `All` に設定されている場合は、*MyActivity* だけでなく、*Activity1* と *Activity2* の各アクティビティについても、追跡レコードが生成されます。  
  
 `implementationVisibility` フラグは、次の追跡レコード タイプに適用されます。  
  
-   ActivityStateRecord  
  
-   FaultPropagationRecord  
  
-   CancelRequestedRecord  
  
-   ActivityScheduledRecord  
  
> [!NOTE]
>  アクティビティの実装から生成される CustomTrackingRecords は、implementationVisibility 設定によるフィルター処理で除外されません。  
  
 `implementationVisibility` 機能は、次のようにコードの追跡プロファイルで <xref:System.Activities.Tracking.ImplementationVisibility> と指定されます。  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
  
```  
  
 The `implementationVisibility` 機能の指定は、次のように構成ファイルの追跡プロファイルで <xref:System.Activities.Tracking.ImplementationVisibility> として指定されます。  
  
```  
<tracking>  
      <profiles>  
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">  
          <workflow activityDefinitionId="*">  
...  
         </workflow>  
        </trackingProfile>  
      </profiles>  
</tracking>  
  
```  
  
 追跡プロファイルの `ImplementationVisibility` 設定は必要に応じて行います。既定では、この値は `RootScope` に設定されます。この属性の値も、大文字と小文字が区別されます。  
  
### プロファイルのクエリの型の追跡  
 追跡プロファイルは、特定の追跡レコードを対象としてワークフロー ランタイムをクエリすることができる追跡レコードの宣言型のサブスクリプションとして構築されます。クエリには、<xref:System.Activities.Tracking.TrackingRecord> オブジェクトのさまざまなクラスを定期受信できる型がいくつかあります。追跡プロファイルは、構成で指定したり、コードで指定したりすることができます。最も一般的なクエリの型は次のとおりです。  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceQuery> \- 前に説明した `Started` や `Completed` など、ワークフロー インスタンスのライフサイクルの変化を追跡するために使用します。<xref:System.Activities.Tracking.WorkflowInstanceQuery> は、次の <xref:System.Activities.Tracking.TrackingRecord> オブジェクトの定期受信に使用されます。  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     定期受信可能な状態は、<xref:System.Activities.Tracking.WorkflowInstanceStates> クラスで指定します。  
  
     <xref:System.Activities.Tracking.WorkflowInstanceQuery> を使用して `Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信するために使用される構成またはコードを、次の例に示します。  
  
    ```  
    <workflowInstanceQueries>  
        <workflowInstanceQuery>  
          <states>  
            <state name="Started"/>  
          </states>  
        </workflowInstanceQuery>  
    </workflowInstanceQueries>  
  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new WorkflowInstanceQuery()  
            {  
                States = { WorkflowInstanceStates.Started}                                                                     
            }  
        }  
    };  
  
    ```  
  
-   <xref:System.Activities.Tracking.ActivityStateQuery> \- ワークフロー インスタンスを構成するアクティビティのライフ サイクルの変化を追跡するために使用します。たとえば、ワークフロー インスタンスの "電子メール送信" アクティビティの完了を毎回追跡する必要がある場合があります。このクエリは、<xref:System.Activities.Tracking.TrackingParticipant> が <xref:System.Activities.Tracking.ActivityStateRecord> オブジェクトを定期受信するのに必要です。定期受信可能な状態は <xref:System.Activities.Tracking.ActivityStates> で指定します。  
  
     `SendEmailActivity` アクティビティに <xref:System.Activities.Tracking.ActivityStateQuery> を使用するアクティビティ状態の追跡レコードを定期受信するために使用される構成またはコードを、次の例に示します。  
  
    ```  
    <activityStateQueries>  
      <activityStateQuery activityName="SendEmailActivity">  
        <states>  
          <state name="Closed"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new ActivityStateQuery()  
            {                              
                ActivityName = "SendEmailActivity",  
                States = { ActivityStates.Closed }  
            }  
        }  
    };  
  
    ```  
  
    > [!NOTE]
    >  複数の activityStateQuery 要素が同じ名前である場合、最後の要素の状態のみが追跡プロファイルで使用されます。  
  
-   <xref:System.Activities.Tracking.ActivityScheduledQuery> \- このクエリを使用すると、親アクティビティによって実行がスケジュールされているアクティビティを追跡できます。このクエリは、<xref:System.Activities.Tracking.TrackingParticipant> が <xref:System.Activities.Tracking.ActivityScheduledRecord> オブジェクトを定期受信するのに必要です。  
  
     <xref:System.Activities.Tracking.ActivityScheduledQuery> を使用して、スケジュールされている `SendEmailActivity` 子アクティビティに関連するレコードを定期受信するために使用される構成またはコードを、次の例に示します。  
  
    ```  
    <activityScheduledQueries>  
      <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
     </activityScheduledQueries>  
  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new ActivityScheduledQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
  
    ```  
  
-   <xref:System.Activities.Tracking.FaultPropagationQuery> \- アクティビティ内で発生したエラーの処理を追跡するために使用します。このクエリは、<xref:System.Activities.Tracking.TrackingParticipant> が <xref:System.Activities.Tracking.FaultPropagationRecord> オブジェクトを定期受信するのに必要です。  
  
     <xref:System.Activities.Tracking.FaultPropagationQuery> を使用して、エラー伝達に関連するレコードを定期受信するために使用される構成またはコードを、次の例に示します。  
  
    ```  
    <faultPropagationQueries>  
      <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />  
    </faultPropagationQueries>  
  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new FaultPropagationQuery()  
            {  
                FaultSourceActivityName = "SendEmailActivity",  
                FaultHandlerActivityName = "NotificationsFaultHandler"  
            }  
        }  
    };  
  
    ```  
  
-   <xref:System.Activities.Tracking.CancelRequestedQuery> \- 親アクティビティによって子アクティビティをキャンセルする要求を追跡するために使用されます。このクエリは、<xref:System.Activities.Tracking.TrackingParticipant> が <xref:System.Activities.Tracking.CancelRequestedRecord> オブジェクトを定期受信するのに必要です。  
  
     <xref:System.Activities.Tracking.CancelRequestedQuery> を使用して、アクティビティのキャンセルに関連するレコードを定期受信するために使用される構成またはコードを、次の例に示します。  
  
    ```  
    <cancelRequestedQueries>  
      <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
    </cancelRequestedQueries>  
  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CancelRequestedQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
  
    ```  
  
-   <xref:System.Activities.Tracking.CustomTrackingQuery> \- コード アクティビティで定義するイベントを追跡するために使用します。このクエリは、<xref:System.Activities.Tracking.TrackingParticipant> が <xref:System.Activities.Tracking.CustomTrackingRecord> オブジェクトを定期受信するのに必要です。  
  
     <xref:System.Activities.Tracking.CustomTrackingQuery> を使用して、カスタム追跡レコードに関連するレコードを定期受信するために使用される構成またはコードを、次の例に示します。  
  
    ```  
    <customTrackingQueries>  
      <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />  
    </customTrackingQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CustomTrackingQuery()   
            {  
                Name = "EmailAddress",  
                ActivityName = "SendEmailActivity"  
            }  
        }  
    };  
  
    ```  
  
-   <xref:System.Activities.Tracking.BookmarkResumptionQuery> \- ワークフロー インスタンス内のブックマークの再開を追跡するために使用します。このクエリは、<xref:System.Activities.Tracking.TrackingParticipant> が <xref:System.Activities.Tracking.BookmarkResumptionRecord> オブジェクトを定期受信するのに必要です。  
  
     <xref:System.Activities.Tracking.BookmarkResumptionQuery> を使用して、ブックマークの再開に関連するレコードを定期受信するために使用される構成またはコードを、次の例に示します。  
  
    ```  
    <bookmarkResumptionQueries>  
      <bookmarkResumptionQuery name="SentEmailBookmark" />  
    </bookmarkResumptionQueries>  
  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new BookmarkResumptionQuery()  
            {  
                Name = "sentEmailBookmark"  
            }  
        }  
    };  
  
    ```  
  
### 注釈  
 注釈を使用すると、ビルド後に構成できる値を使用して、追跡レコードへのタグ付けを任意に行うことができます。たとえば、複数のワークフローに存在する複数の追跡レコードに、"Mail Server" \=\= "Mail Server1" というタグを付けることができます。こうすると、後で追跡レコードのクエリを実行するときに、このタグの付いたすべてのレコードを簡単に見つけることができます。  
  
 これを可能にするために、次の例に示すように注釈が追跡クエリに追加されます。  
  
```  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
  
```  
  
### 追跡プロファイルを作成する方法  
 追跡クエリ要素を使用することで、XML 構成ファイル、または [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] のコードを使用した追跡プロファイルを作成できます。次の例は、構成ファイルを使用して作成した追跡プロファイルです。  
  
```  
<system.serviceModel>  
  <tracking>  
    <profiles>  
      <trackingProfile name="Sample Tracking Profile ">  
        <workflow activityDefinitionId="*">  
          <!--Specify the tracking profile query elements to subscribe for tracking records-->  
        </workflow>  
      </trackingProfile>  
    </profiles>  
  </tracking>  
</system.serviceModel>  
  
```  
  
> [!WARNING]
>  ワークフロー サービス ホストを使用する WF の場合、追跡プロファイルは構成ファイルを使用して作成されることがほとんどです。また、追跡プロファイルや追跡クエリ API を使用するコードで追跡プロファイルを作成することも可能です。  
  
 XML 構成ファイルとして構成されるプロファイルは、動作拡張を使用して追跡参加要素に適用されます。後のセクション「[ワークフローの追跡の構成](../../../docs/framework/windows-workflow-foundation//configuring-tracking-for-a-workflow.md)」で説明されているように、これは WorkflowServiceHost に追加されます。  
  
 ホストが生成する追跡レコードの詳細度は、追跡プロファイルの構成の設定によって決まります。追跡参加要素は、クエリを追跡プロファイルに追加して追跡レコードを定期受信します。すべての追跡レコードを定期受信するためには、追跡プロファイルにおいて各クエリの名前フィールドで “\*” を使用し、すべての追跡クエリを指定する必要があります。  
  
 一般的な追跡プロファイルの例を次に示します。  
  
-   ワークフロー インスタンスのレコードとエラーを取得する追跡プロファイル  
  
```  
<trackingProfile name="Instance and Fault Records">  
  <workflow activityDefinitionId="*">  
    <workflowInstanceQueries>  
      <workflowInstanceQuery>  
        <states>  
          <state name="*" />  
        </states>  
      </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    <activityStateQueries>  
      <activityStateQuery activityName="*">  
        <states>  
          <state name="Faulted"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
  </workflow>  
</trackingProfile>  
  
```  
  
1.  すべてのカスタム追跡レコードを取得する追跡プロファイル  
  
```  
<trackingProfile name="Instance_And_Custom_Records">  
  <workflow activityDefinitionId="*">  
    <customTrackingQueries>  
      <customTrackingQuery name="*" activityName="*" />  
    </customTrackingQueries>  
  </workflow>  
</trackingProfile>  
  
```  
  
## 参照  
 [SQL 追跡](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)   
 [Windows Server App Fabric の監視](http://go.microsoft.com/fwlink/?LinkId=201273)   
 [App Fabric を使用したアプリケーションの監視](http://go.microsoft.com/fwlink/?LinkId=201275)