---
title: "エラー コントラクト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# エラー コントラクト
エラー コントラクトのサンプルでは、エラー情報をサービスからクライアントに通信する方法を示します。  サンプルは、「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づき、内部例外をエラーに変換するいくつかの追加コードをサービスに追加しています。  クライアントは 0 による除算を試行し、サービスを強制的にエラー状態にします。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 電卓コントラクトは、<xref:System.ServiceModel.FaultContractAttribute> が含まれるように変更されています。次のサンプル コードを参照してください。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <xref:System.ServiceModel.FaultContractAttribute> 属性は、`Divide` 操作が型 `MathFault` のエラーを返すことができることを示します。  シリアル化可能な任意の型のエラーが発生します。  この場合、`MathFault` は次のようなデータ コントラクトになります。  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
  
```  
  
 0 による除算の例外が発生すると、`Divide` メソッドは <xref:System.ServiceModel.FaultException%601> 例外をスローします。次のサンプル コードを参照してください。  この例外により、クライアントにエラーが送信されます。  
  
```  
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 クライアント コードは、0 による除算を要求することで強制的にエラーを発生させます。  このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。  0 による除算がエラーとして報告されたことが示されます。  クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 クライアントでこれを行うには、適切な `FaultException<MathFault>` 例外を次のようにキャッチします。  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 既定では、サービス実装の詳細がサービスのセキュリティの境界から漏えいするのを回避するため、予期しない例外の詳細はクライアントに送信されません。  `FaultContract` では、コントラクトでエラーを説明し、例外の特定の型がクライアントへの転送に適しているとマークできます。  `FaultException<T>` には、エラーをコンシューマーに送信するためのランタイム機構が用意されています。  
  
 ただし、デバッグ時にはサービス エラーの内部詳細を確認することが役立ちます。  前に説明したセキュリティ動作を無効にするには、サーバーで未処理のすべての例外の詳細を、クライアントに送信するエラーに含めるように指定できます。  これは、<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> を `true` に設定することによって行います。  次の例に示すように、コードまたは構成のどちらを使用しても設定できます。  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 さらに、サービスの `behaviorConfiguration` 属性を構成ファイルで “CalculatorServiceBehavior” に設定し、動作をサービスに関連付ける必要があります。  
  
 こうしたエラーをクライアントでキャッチするには、非ジェネリックの <xref:System.ServiceModel.FaultException> をキャッチする必要があります。  
  
 この動作はデバッグ目的でのみ使用し、製品版では有効にしないでください。  
  
### サンプルをセットアップ、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」に移動して、すべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルおよび [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## 参照