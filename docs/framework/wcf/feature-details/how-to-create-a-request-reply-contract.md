---
title: "方法 : 要求/応答コントラクトを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# 方法 : 要求/応答コントラクトを作成する
要求\/応答コントラクトは、応答を返すメソッドを指定します。応答が送信され、このコントラクトの条件の下で要求に関連付けられる必要があります。メソッドが応答を返さない場合 \(C\# の場合は `void` または Visual Basic の場合は `Sub`\) でも、インフラストラクチャは、空のメッセージを作成して送信することで、メソッドが返ったことを呼び出し元に示します。空の応答メッセージが送信されるのを防ぐには、操作で 1 方向コントラクトを使用します。  
  
### 要求\/応答コントラクトを作成するには  
  
1.  選択したプログラミング言語でインターフェイスを作成します。  
  
2.  インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> 属性を適用します。  
  
3.  クライアントが呼び出すことのできる各メソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性を適用します。  
  
4.  省略可能。<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティの値を `true` に設定して、空の応答メッセージが送信されることを防止します。既定では、すべての操作は要求\/応答コントラクトです。  
  
## 使用例  
 次のサンプルは、`Add` メソッドと `Subtract` メソッドを提供する電卓サービスのコントラクトを定義します。`Multiply` メソッドは <xref:System.ServiceModel.OperationContractAttribute> クラスでマークされていないため、このコントラクトの一部ではありません。したがって、クライアントからはアクセスできません。  
  
```  
using System.ServiceModel;   
  
[ServiceContract]   
public interface ICalculator   
{   
[OperationContract]   
// It would be equivalent to write explicitly:  
// [OperationContract(IsOneWay=false)]   
int Add(int a, int b);   
  
[OperationContract]   
int Subtract(int a, int b);   
  
int Multiply(int a, int b)  
}  
```  
  
-   操作コントラクトを指定する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、<xref:System.ServiceModel.OperationContractAttribute> クラスおよび <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティのトピックを参照してください。  
  
-   <xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性を適用すると、サービスを展開した後に Web サービス記述言語 \(WSDL\) ドキュメントでサービス コントラクト定義が自動的に生成されます。ドキュメントは、サービスの HTTP ベース アドレスに `?wsdl` を付け加えてしてダウンロードできます。たとえば、「`http://microsoft/CalculatorService?wsdl`」と入力します。  
  
## 参照  
 <xref:System.ServiceModel.OperationContractAttribute>   
 [サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)   
 [方法 : 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)