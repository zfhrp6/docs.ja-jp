---
title: "方法 : サービス コントラクトでのエラーを宣言する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 方法 : サービス コントラクトでのエラーを宣言する
マネージ コードでは、エラー条件が発生すると例外がスローされます。  しかし [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションでは、サービス コントラクトで SOAP エラーを宣言することにより、どのエラー情報をクライアントに通知するかを指定するようになっています。  例外とエラーの関係の概要については、「[コントラクトおよびサービスのエラーの指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)」を参照してください。  
  
### SOAP エラーを指定するサービス コントラクトを作成する  
  
1.  サービス コントラクトを作成し、操作をいくつか定義します。  例については、「[方法 : サービス コントラクトを定義する](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)」を参照してください。  
  
2.  操作を選択します。これに対して指定したエラー条件が発生したとき、クライアント側に通知することになります。  どのようなエラー条件を SOAP エラーとしてクライアントに通知する必要があるかについては、「[コントラクトおよびサービスのエラーの指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)」を参照してください。  
  
3.  選択した操作に対して <xref:System.ServiceModel.FaultContractAttribute?displayProperty=fullName> 属性を適用し、シリアル化可能なエラー型をコンストラクターに渡します。  シリアル化可能な型の作成方法および使用方法の詳細については、「[サービス コントラクトでのデータ転送の指定](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)」を参照してください。  `SampleMethod` 操作で `GreetingFault` を返せるように指定する例を次に示します。  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  コントラクト内でクライアントへの通知が必要な操作すべてについて、手順 2. および 3. を繰り返します。  
  
## 指定した SOAP エラーを返す操作の実装  
 エラー状態を呼び出し元アプリケーションに通知するために、前の手順で指定したような特定の SOAP エラーを操作中に返せるように指定したので、次に実際に通知処理を実装します。  
  
#### 指定した SOAP エラーを操作中に例外としてスローする  
  
1.  操作中に <xref:System.ServiceModel.FaultContractAttribute> で指定したエラー条件が発生したとき、<xref:System.ServiceModel.FaultException%601?displayProperty=fullName> 例外を生成してスローする、というコードを記述します。SOAP エラーは型パラメーターとして、生成する例外に渡します。  前の手順で示した `SampleMethod` 内で `GreetingFault` 例外をスローするコード例を次に示します。  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## 使用例  
 `SampleMethod` 操作内で `GreetingFault` エラーが発生した場合の処理を実装したコード例を次に示します。  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## 参照  
 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=fullName>   
 <xref:System.ServiceModel.FaultException%601?displayProperty=fullName>