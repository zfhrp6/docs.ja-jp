---
title: "方法: Windows サービスを一時中断する (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: d44358d3f76f50a06ede5e7d720f4f48d80893de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>方法: Windows サービスを一時中断する (Visual Basic)
この例では、<xref:System.ServiceProcess.ServiceController>コンポーネントがローカル コンピューター上の IIS 管理サービスを一時停止します。  
  
## <a name="example"></a>例  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 このコード例は、IntelliSense コード スニペットとしても利用できます。 配置されているコード スニペット ピッカーで**Windows オペレーティング システム > Windows サービス**です。 詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.serviceprocess.dll へのプロジェクト参照。  
  
-   <xref:System.ServiceProcess> 名前空間のメンバーへのアクセス許可。 コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A>のプロパティ、<xref:System.ServiceProcess.ServiceController>クラスは既定では、ローカル コンピューターです。 別のコンピューターで Windows サービスを参照するには、変更、<xref:System.ServiceProcess.ServiceController.MachineName%2A>プロパティをそのコンピューターの名前にします。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   サービスを一時停止することはできません。 (<xref:System.InvalidOperationException>)  
  
-   システム API にアクセス中にエラーが発生しました。 (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 使用して、コンピューター上のサービスのコントロールを制限できる、<xref:System.ServiceProcess.ServiceControllerPermissionAccess>アクセス許可を設定、<xref:System.ServiceProcess.ServiceControllerPermission>です。  
  
 使用してサービスの情報へのアクセスを制限することがあります、<xref:System.Security.Permissions.PermissionState>アクセス許可を設定、<xref:System.Security.Permissions.SecurityPermission>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [方法: Windows サービス (Visual Basic) を続行](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
