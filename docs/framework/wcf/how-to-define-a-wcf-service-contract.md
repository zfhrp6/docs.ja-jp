---
title: "方法 : Windows Communication Foundation サービス コントラクトを定義する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "サービス コントラクト [WCF], 定義"
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: 58
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 58
---
# 方法 : Windows Communication Foundation サービス コントラクトを定義する
これは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションの作成に必要な 6 つのタスクのうち、1 番目のタスクです。6 つのすべてのタスクの概要については、「[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを作成する場合、まずサービス コントラクトを定義します。サービス コントラクトは、サービスがサポートする操作を指定します。操作は Web サービス メソッドと見なすことができます。コントラクトは C\+\+、C\#、または Visual Basic \(VB\) インターフェイスを定義することで作成します。インターフェイスの各メソッドは、特定のサービス操作に対応しています。各インターフェイスには <xref:System.ServiceModel.ServiceContractAttribute> が適用されており、各操作には <xref:System.ServiceModel.OperationContractAttribute> 属性が適用されている必要があります。<xref:System.ServiceModel.ServiceContractAttribute> 属性を持つインターフェイス内のメソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性がない場合、そのメソッドはサービスによって公開されません。  
  
 手順の後に、このタスクに使用するコード例を示します。  
  
### サービス コントラクトを定義するには  
  
1.  **\[スタート\]** メニューで [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を右クリックし、**\[管理者として実行\]** をクリックして、管理者としてプログラムを開きます。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントして **\[プロジェクト\]** をクリックすることにより、WCF サービス ライブラリ プロジェクトを作成します。**\[新しいプロジェクト\]** ダイアログで、左側の **\[Visual C\#\]** \(C\# プロジェクトの場合\) を展開するか、または **\[他の言語\]** を展開し、**\[Visual Basic\]** \(Visual Basic プロジェクトの場合\) を展開します。選択した言語の **\[WCF\]** を選択します。プロジェクト テンプレートの一覧がダイアログの中央部分に表示されます。**\[WCF サービス ライブラリ\]** を選択します。**\[名前\]** ボックスに「`GettingStartedLib`」と入力し、ダイアログの最下部の **\[ソリューション名\]** ボックスに「`GettingStarted`」と入力します。  
  
3.  Visual Studio により、IService1.cs \(または IService1.vb\)、Service1.cs \(または Service1.vb\)、App.config の 3 つのファイルを含むプロジェクトが作成されます。IService1 ファイルには、既定のサービス コントラクトが含まれています。Service1 ファイルには、サービス コントラクトの既定の実装が含まれています。App.config ファイルには、Visual Studio WCF サービス ホストに既定のサービスを読み込むために必要な構成が含まれています。WCF サービス ホスト ツールの詳細については、「[WCF サービス ホスト \(WcfSvcHost.exe\)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)」を参照してください。  
  
4.  IService1.cs または IService1.vb ファイルを開き、名前空間の宣言を残したまま、名前空間宣言内のコードを削除します。次のコードに示すように、名前空間宣言内に新しいインターフェイス `ICalculator` を定義します。  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
    namespace GettingStartedLib  
    {  
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
            public interface ICalculator  
            {  
                [OperationContract]  
                double Add(double n1, double n2);  
                [OperationContract]  
                double Subtract(double n1, double n2);  
                [OperationContract]  
                double Multiply(double n1, double n2);  
                [OperationContract]  
                double Divide(double n1, double n2);  
            }  
    }  
  
    ```  
  
    ```  
    ‘IService.vb  
    Imports System  
    Imports System.ServiceModel  
  
    Namespace GettingStartedLib  
  
        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
        Public Interface ICalculator  
  
            <OperationContract()> _  
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
        End Interface  
    End Namespace  
  
    ```  
  
     このコントラクトは、オンライン電卓を定義します。`ICalculator` インターフェイスは <xref:System.ServiceModel.ServiceContractAttribute> 属性でマークされています。この属性は、コントラクト名を区別するために使用される名前空間を定義します。各電卓操作は <xref:System.ServiceModel.OperationContractAttribute> 属性でマークされています。  
  
    > [!NOTE]
    >  属性を使用してインターフェイス、メンバー、またはクラスに注釈を付けるときは、属性名から "Attribute" 部分を削除できます。したがって、<xref:System.ServiceModel.ServiceContractAttribute> は、C\# では `[ServiceContract]`、Visual Basic では `<ServiceContract>` になります。  
  
## 参照  
 <xref:System.ServiceModel.ServiceContractAttribute>   
 <xref:System.ServiceModel.OperationContractAttribute>   
 [方法 : サービス コントラクトを実装する](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)   
 [概要](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)