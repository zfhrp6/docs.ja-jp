---
title: "方法: Windows サービスを続行する (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 73b16a5e5834f7279ae551d4e7efd26cc86c1d07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>方法: Windows サービスを続行する (Visual Basic)
この例では、<xref:System.ServiceProcess.ServiceController>コンポーネントをローカル コンピューターで、IIS Admin サービスを続行します。  
  
## <a name="example"></a>例  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 このコード例は、IntelliSense コード スニペットとしても利用できます。 配置されているコード スニペット ピッカーで**Windows オペレーティング システム > Windows サービス**です。 詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.serviceprocess.dll へのプロジェクト参照。  
  
-   <xref:System.ServiceProcess> 名前空間のメンバーへのアクセス許可。 コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A>のプロパティ、<xref:System.ServiceProcess.ServiceController>クラスは既定では、ローカル コンピューターです。 別のコンピューターで Windows サービスを参照するには、変更、<xref:System.ServiceProcess.ServiceController.MachineName%2A>プロパティをそのコンピューターの名前にします。  
  
 呼び出すことはできません、<xref:System.ServiceProcess.ServiceController.Continue%2A>サービス コント ローラーの状態になるまで、サービスに対してメソッド<xref:System.ServiceProcess.ServiceControllerStatus.Paused>です。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   サービスを再開することはできません。 (<xref:System.InvalidOperationException>)  
  
-   システム API にアクセス中にエラーが発生しました。 (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 使用して、コンピューター上のサービスのコントロールを制限できる、<xref:System.ServiceProcess.ServiceControllerPermissionAccess>列挙型のアクセス許可設定を<xref:System.ServiceProcess.ServiceControllerPermission>クラスです。  
  
 使用してサービスの情報へのアクセスを制限することがあります、<xref:System.Security.Permissions.PermissionState>列挙型のアクセス許可設定を<xref:System.Security.Permissions.SecurityPermission>クラスです。  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [方法 : Windows サービスを一時中断する (Visual Basic)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
