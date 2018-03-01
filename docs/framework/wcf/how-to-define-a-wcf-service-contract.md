---
title: "方法 : Windows Communication Foundation サービス コントラクトを定義する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c69f79d8629acee80a2e59346032e7733ec37dea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>方法 : Windows Communication Foundation サービス コントラクトを定義する
これは、基本的な [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションの作成に必要な 6 つのタスクのうちの最初のタスクです。 タスクの 6 つのすべての概要については、次を参照してください。、[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)トピックです。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを作成する場合、まずサービス コントラクトを定義します。 サービス コントラクトは、サービスがサポートする操作を指定します。 操作は Web サービス メソッドと見なすことができます。 コントラクトは C++、C#、または Visual Basic (VB) インターフェイスを定義することで作成します。 インターフェイスの各メソッドは、特定のサービス操作に対応しています。 各インターフェイスには <xref:System.ServiceModel.ServiceContractAttribute> が適用されており、各操作には <xref:System.ServiceModel.OperationContractAttribute> 属性が適用されている必要があります。 <xref:System.ServiceModel.ServiceContractAttribute> 属性を持つインターフェイス内のメソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性がない場合、そのメソッドはサービスによって公開されません。  
  
 手順の後に、このタスクに使用するコード例を示します。  
  
### <a name="to-define-a-service-contract"></a>サービス コントラクトを定義するには  
  
1.  開いている[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]でプログラムを右クリックして、管理者として、**開始**メニューを選択して**管理者として実行**です。  
  
2.  クリックして、WCF サービス ライブラリ プロジェクトを作成、**ファイル**メニューを選択して**新規**、**プロジェクト**です。 **新しいプロジェクト**ダイアログ ボックスで、ダイアログ ボックスの左側にある展開**Visual c#** c# プロジェクトまたは**他の言語**し**Visual Basic** Visual Basic プロジェクト。 選択した言語を選択**WCF**とプロジェクト テンプレートの一覧がダイアログの中央のセクションに表示されます。 選択**WCF サービス ライブラリ**、および種類`GettingStartedLib`で、**名前** テキスト ボックスと`GettingStarted`で、**ソリューション名**ダイアログの下部にあるテキスト ボックス。  
  
3.  Visual Studio により、IService1.cs (または IService1.vb)、Service1.cs (または Service1.vb)、App.config の 3 つのファイルを含むプロジェクトが作成されます。IService1 ファイルには、既定のサービス コントラクトが含まれています。  Service1 ファイルには、サービス コントラクトの既定の実装が含まれています。 App.config ファイルには、Visual Studio WCF サービス ホストに既定のサービスを読み込むために必要な構成が含まれています。 WCF サービス ホスト ツールの詳細については、次を参照してください[WCF サービス ホスト (WcfSvcHost.exe)。](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
4.  IService1.cs または IService1.vb ファイルを開き、名前空間の宣言を残したまま、名前空間宣言内のコードを削除します。 次のコードに示すように、名前空間宣言内に新しいインターフェイス `ICalculator` を定義します。  
  
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
  
     このコントラクトは、オンライン電卓を定義します。 `ICalculator` インターフェイスは <xref:System.ServiceModel.ServiceContractAttribute> 属性でマークされています。 この属性は、コントラクト名を区別するために使用される名前空間を定義します。 各電卓操作は <xref:System.ServiceModel.OperationContractAttribute> 属性でマークされています。  
  
    > [!NOTE]
    >  属性を使用してインターフェイス、メンバー、またはクラスに注釈を付けるときは、属性名から "Attribute" 部分を削除できます。 したがって、<xref:System.ServiceModel.ServiceContractAttribute> は、C# では `[ServiceContract]`、Visual Basic では `<ServiceContract>` になります。  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [方法: サービス コントラクトを実装する](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [はじめに](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)
