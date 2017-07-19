---
title: "方法: Windows サービスを一時中断する (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ServiceController.Pause"
helpviewer_keywords: 
  - "一時停止 (Windows サービス アプリケーションを)"
  - "Windows サービス アプリケーション, 一時中断"
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 15
---
# 方法: Windows サービスを一時中断する (Visual Basic)
次に示すのは、<xref:System.ServiceProcess.ServiceController> コンポーネントを使用して、ローカル コンピューターの IIS Admin サービスを一時中断する例です。  
  
## 使用例  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、このコードは、**\[Windows オペレーティング システム\] \> \[Windows サービス\]** にあります。  詳細については、「[コード スニペット](../Topic/Code%20Snippets.md)」を参照してください。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.serviceprocess.dll に対するプロジェクト参照。  
  
-   <xref:System.ServiceProcess> 名前空間のメンバーに対するアクセス。  コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。  詳細については、「[Imports Statement \(.NET Namespace and Type\)](../../../ocs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## 信頼性の高いプログラミング  
 <xref:System.ServiceProcess.ServiceController> クラスの <xref:System.ServiceProcess.ServiceController.MachineName%2A> プロパティは、既定ではローカル コンピューターに設定されています。  他のコンピューターの Windows サービスを参照するには、<xref:System.ServiceProcess.ServiceController.MachineName%2A> プロパティを目的のコンピューター名に変更します。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   サービスが一時中断できない場合  \([InvalidOperationException クラス](frlrfSystemInvalidOperationExceptionClassTopic)\)  
  
-   システム API へのアクセスでエラーが発生した場合  \([Win32Exception クラス](frlrfSystemComponentModelWin32ExceptionClassTopic)\)  
  
## .NET Framework セキュリティ  
 [ServiceControllerPermissionAccess 列挙体](frlrfSystemServiceProcessServiceControllerPermissionAccessClassTopic)を使用して[ServiceControllerPermission クラス](frlrfSystemServiceProcessServiceControllerPermissionClassTopic)でアクセス許可を設定することにより、使用するコンピューターのサービスに対する制御を制限できます。  
  
 [PermissionState 列挙体](frlrfSystemSecurityPermissionsPermissionStateClassTopic)を使用して [SecurityPermission クラス](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic)でアクセス許可を設定することにより、サービス情報へのアクセスを制限できます。  
  
## 参照  
 <xref:System.ServiceProcess.ServiceController>   
 <xref:System.ServiceProcess.ServiceControllerStatus>   
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>   
 [方法: Windows サービスを続行する \(Visual Basic\)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)