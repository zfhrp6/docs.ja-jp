---
title: "サービス アプリケーションのプログラミング アーキテクチャ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e9c16f2e603a3ce9bbc59be4e01aa492239d2c63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="service-application-programming-architecture"></a>サービス アプリケーションのプログラミング アーキテクチャ
継承するクラスに基づいて Windows サービス アプリケーション、<xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>クラスです。 このクラスからメソッドをオーバーライドして、サービスの動作を決定するそれらの機能を定義します。  
  
 サービスの作成に関連する主要なクラスは次のとおりです。  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>— メソッドをオーバーライドする、<xref:System.ServiceProcess.ServiceBase>クラスのサービスを作成するときに、このサービス関数がクラスを継承する方法を決定するコードを定義します。  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType><xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> -これらのクラスを使用してインストールし、サービスをアンインストールします。  
  
 さらに、クラスの名前付き<xref:System.ServiceProcess.ServiceController>サービス自体を操作するために使用できます。 このクラスは、サービスの作成に関連するではありませんを開始し、サービスを停止し、コマンドを渡す、一連の列挙体を返すために使用できます。  
  
## <a name="defining-your-services-behavior"></a>サービスの動作を定義します。  
 サービス クラスでは、サービス コントロール マネージャーで、サービスの状態が変更されたときの動作を決定する基底クラスの関数をオーバーライドします。 <xref:System.ServiceProcess.ServiceBase>クラスは次のメソッドは、カスタム動作を追加するをオーバーライドすることができますを公開します。  
  
|メソッド|する上書き|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|サービスが実行を開始するときに、どのようなアクションを実行する必要がありますを指定します。 有効な作業を実行するようにサービスに対してこの手順でコードを記述する必要があります。|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|サービスが一時停止したときの動作を示してください。|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|サービスの実行が停止したときの動作を示してください。|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|サービスが一時停止された後に正常な機能を再開したときの動作を示してください。|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|その時点で、サービスが実行されている場合、システムがシャット ダウンする直前の動作を示します。|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|サービスは、カスタム コマンドを受信したときの動作を示してください。 カスタム コマンドの詳細については、オンライン MSDN 参照してください。|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|バッテリ低下や中断された操作など、電源管理イベントを受信したときに、サービスの応答方法を示してください。|  
  
> [!NOTE]
>  これらのメソッドは、サービスがその有効期間内に通過状態を表しています。サービスは、1 つの状態から、次に遷移します。 応答するサービスを決して取得するなど、<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>する前にコマンド<xref:System.ServiceProcess.ServiceBase.OnStart%2A>呼び出されました。  
  
 その他のいくつかのプロパティと関心のあるメソッドがあります。 以下に例を示します。  
  
-   <xref:System.ServiceProcess.ServiceBase.Run%2A>メソッドを<xref:System.ServiceProcess.ServiceBase>クラスです。 これは、サービスのメイン エントリ ポイントです。 アプリケーションのコードが挿入される Windows サービス テンプレートを使用してサービスを作成するときに`Main`メソッドをサービスを実行します。 このコードは、次のようになります。  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  これらの例は、型の配列を使用して<xref:System.ServiceProcess.ServiceBase>をアプリケーションに含まれる各サービスを追加することができます、し、すべてのサービスで一緒に実行できます。 1 つのサービスのみを作成する場合は、ただし、こともできましていないを使用して、配列から継承する新しいオブジェクトを単に宣言<xref:System.ServiceProcess.ServiceBase>し、実行します。 例については、次を参照してください。[する方法: プログラムによってサービスを書き込む](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)です。  
  
-   一連のプロパティの<xref:System.ServiceProcess.ServiceBase>クラスです。 これらは、どのような方法は、サービスを呼び出すことができますを決定します。 たとえばときに、<xref:System.ServiceProcess.ServiceBase.CanStop%2A>プロパティに設定されている`true`、<xref:System.ServiceProcess.ServiceBase.OnStop%2A>サービスでメソッドを呼び出すことができます。 ときに、<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>プロパティに設定されている`true`、<xref:System.ServiceProcess.ServiceBase.OnPause%2A>と<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>メソッドを呼び出すことができます。 これらのプロパティのいずれかを設定すると`true`、しをオーバーライドし、関連するメソッドの処理を定義する必要があります。  
  
    > [!NOTE]
    >  サービスをオーバーライドする必要がありますには、少なくとも<xref:System.ServiceProcess.ServiceBase.OnStart%2A>と<xref:System.ServiceProcess.ServiceBase.OnStop%2A>を有効にします。  
  
 呼ばれるコンポーネントを使用することも、<xref:System.ServiceProcess.ServiceController>と通信して、既存のサービスの動作を制御します。  
  
## <a name="see-also"></a>関連項目  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [方法: Windows サービスの作成](../../../docs/framework/windows-services/how-to-create-windows-services.md)
