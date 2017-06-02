---
title: "方法: Windows サービスを続行する (Visual Basic) | Microsoft Docs"
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
  - "ServiceController.Continue"
helpviewer_keywords: 
  - "一時停止 (Windows サービス アプリケーションを)"
  - "Windows サービス アプリケーション, 一時中断"
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
caps.latest.revision: 16
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 16
---
# 方法: Windows サービスを続行する (Visual Basic)
次に示すのは、<xref:System.ServiceProcess.ServiceController> コンポーネントを使用して、ローカル コンピューターの IIS Admin サービスを続行する例です。  
  
## 使用例  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、このコードは、**\[Windows オペレーティング システム\] \> \[Windows サービス\]** にあります。  詳細については、「[コード スニペット](../Topic/Code%20Snippets.md)」を参照してください。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.serviceprocess.dll に対するプロジェクト参照。  
  
-   <xref:System.ServiceProcess> 名前空間のメンバーに対するアクセス。  コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。  詳細については、「[Imports Statement \(.NET Namespace and Type\)](../../../ocs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## 信頼性の高いプログラミング  
 <xref:System.ServiceProcess.ServiceController> クラスの <xref:System.ServiceProcess.ServiceController.MachineName%2A> プロパティは、既定ではローカル コンピューターに設定されています。  他のコンピューターの Windows サービスを参照するには、<xref:System.ServiceProcess.ServiceController.MachineName%2A> プロパティを目的のコンピューター名に変更します。  
  
 サービス コントローラーのステータスが <xref:System.ServiceProcess.ServiceControllerStatus> になるまでは、そのサービスに対して <xref:System.ServiceProcess.ServiceController.Continue%2A> メソッドを呼び出すことはできません。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   サービスを再開できない場合  \(<xref:System.InvalidOperationException>\)  
  
-   システム API へのアクセスでエラーが発生した場合  \(<xref:System.ComponentModel.Win32Exception>\)  
  
## .NET Framework セキュリティ  
 <xref:System.ServiceProcess.ServiceControllerPermissionAccess> 列挙体を使用して <xref:System.ServiceProcess.ServiceControllerPermission> クラスでアクセス許可を設定することにより、使用するコンピューターのサービスに対する制御を制限できます。  
  
 <xref:System.Security.Permissions.PermissionState> 列挙体を使用して <xref:System.Security.Permissions.SecurityPermission> クラスでアクセス許可を設定することにより、サービス情報へのアクセスを制限できます。  
  
## 参照  
 <xref:System.ServiceProcess.ServiceController>   
 <xref:System.ServiceProcess.ServiceControllerStatus>   
 [方法: Windows サービスを一時中断する \(Visual Basic\)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)