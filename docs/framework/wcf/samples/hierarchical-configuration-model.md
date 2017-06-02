---
title: "階層的な構成モデル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 階層的な構成モデル
このサンプルでは、サービスの構成ファイルの階層を実装する方法を示します。また、バインド、サービス動作、およびエンドポイント動作を階層の上位レベルから継承する方法も示します。  
  
## サンプルの詳細  
 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用に開発された機能の 1 つとして、階層的な構成モデルの強化があります。階層的な構成モデルは、たとえば、Machine.config \-\> Rootweb.config \-\> Web.config のように定義されます。[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] では、構成階層の上位レベルで定義されるこれらのバインドおよび動作が、明示的な構成なしにサービスに追加されます。このサンプルでは、コンピューター レベルまたはアプリケーション レベルで定義された構成要素に依存することによって簡単なサービス構成を実現する方法を示します。  
  
 このサンプルは、階層の 3 つのレベルで定義された 9 個のサービスから構成されます。`Service1` はルートになります。`Service2` と `Service3` は `Service1` から既定の要素を継承します。`Service4`、`Service5`、`Service6`、および `Service7` は、階層の第 3 レベルで定義され、`Service3` から既定の要素を継承します。最後に、`Service10` および `Service11` は階層の第 4 レベルに置かれます。  
  
 すべてのサービスは `IDesc` コントラクトを実装します。`IDesc` インターフェイスの定義を次に示します。この定義は、このインターフェイスで公開されるメソッドを示しています。`IDesc` インターフェイスは Service1.cs で定義されます。  
  
```  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
  
```  
  
 サービスによるこれらのメソッドの実装は単純です。`ListEndpoints` は、すべてのサービス エンドポイントを反復処理し、サービスにあるすべてのエンドポイントのリストを返します。`ListServiceBehaviors` は、サービスに追加されたすべての動作を反復処理し、サービスに関連付けられているすべてのサービス動作のリストを返します。`ListEndpointBehaviors` は、`ListServiceBehaviors` と同様に動作しますが、サービス動作ではなくエンドポイント動作のリストを返します。  
  
 この実装により、クライアントは、サービスで公開されているエンドポイントの数、およびサービスに追加されたサービス動作とエンドポイント動作を認識できます。サンプルの一部として実装されているクライアントは、ソリューションのすべてのサービスにサービス参照を追加し、サービスごとにこれらの要素を示します。  
  
## このサンプルを使用するには  
  
#### クライアントを実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、ConfigHierarchicalModel.sln ファイルを開きます。  
  
2.  クライアント プロジェクトはまだスタートアップ プロジェクトに設定されていないので、次の手順で設定します。  
  
    1.  **ソリューション エクスプローラー**で、ソリューションを右クリックし、**\[プロパティ\]** をクリックします。  
  
    2.  **\[共通プロパティ\]** で、**\[スタートアップ プロジェクト\]** をクリックし、**\[シングル スタートアップ プロジェクト\]** をクリックします。  
  
    3.  **\[シングル スタートアップ プロジェクト\]** ボックスの一覧で、**\[クライアント\]** をクリックします。  
  
    4.  **\[OK\]** をクリックしてダイアログ ボックスを閉じます。  
  
3.  サンプルをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
4.  クライアントを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!NOTE]
>  この手順が機能しない場合は、次の手順を使用して、環境設定が適切であることを確認してください。  
>   
>  1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
> 2.  ソリューションをビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
> 3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## 参照  
 [AppFabric の管理のサンプル](http://go.microsoft.com/fwlink/?LinkId=193960)