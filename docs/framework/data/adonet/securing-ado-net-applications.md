---
title: "ADO.NET アプリケーションのセキュリティ保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0424a92f2308c21404cf35cd59c797498e6af992
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="securing-adonet-applications"></a>ADO.NET アプリケーションのセキュリティ保護
ユーザー入力の検証を怠るなど、コーディング時に陥りやすい基本的なミスを防ぐだけでは、安全な ADO.NET アプリケーションを作成することはできません。 データにアクセスするアプリケーションには、機密データの取得、操作、破壊など、攻撃者に攻略される可能性がある障害点が多数あります。 そのため、アプリケーションの設計フェーズで行う脅威のモデリングのプロセスから、アプリケーションの最終的な配置と継続的な保守に至るまで、セキュリティのすべての側面を理解することが重要です。  
  
 .NET Framework には、データベース アプリケーションのセキュリティを確保し、管理するのに有用なクラス、サービス、およびツールが多数用意されています。 共通言語ランタイム (CLR) によって、コードを実行するためのタイプ セーフな環境が実現され、それと同時に、コード アクセス セキュリティ (CAS) によって、マネージ コードのアクセス許可はより制限されています。 攻撃者によってもたらされる可能性のある損害は、安全なデータ アクセスのためのコーディング方法に従うことによって最小限に抑えることができます。  
  
 データベースなどのアンマネージ リソースを扱う場合、安全なコードを作成したとしても、自ら招いたセキュリティ ホールを防ぐことはできません。 SQL Server を含め、ほとんどのサーバー データベースには、正しく実装することによってセキュリティを強化できる独自のセキュリティ システムがあります。 しかし、データ ソースがいかに堅牢なセキュリティ システムを備えていたとしても、それが適切に構成されていなければ攻撃を防ぐことはできません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [セキュリティの概要](../../../../docs/framework/data/adonet/security-overview.md)  
 安全な ADO.NET アプリケーションを設計するための推奨事項について説明します。  
  
 [安全なデータ アクセス](../../../../docs/framework/data/adonet/secure-data-access.md)  
 セキュリティで保護されたデータ ソースのデータを使用する方法について説明します。  
  
 [安全なクライアント アプリケーション](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 クライアント アプリケーションのセキュリティに関する考慮事項について説明します。  
  
 [コード アクセス セキュリティと ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 CAS を使用して ADO.NET コードを保護する方法について説明します。 部分信頼の使用方法についても説明します。  
  
 [プライバシーとデータ セキュリティ](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 ADO.NET アプリケーションの暗号化オプションについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [SQL Server のセキュリティ](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 開発者の観点から SQL Server のセキュリティ機能について説明します。  
  
 [セキュリティの考慮事項](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 Entity Framework アプリケーションのセキュリティについて説明します。  
  
 [セキュリティ](../../../../docs/standard/security/index.md)  
 .NET Framework のセキュリティをあらゆる観点から説明したトピックへのリンクが含まれています。  
  
 [セキュリティ ツール](http://msdn.microsoft.com/en-us/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 セキュリティ保護およびセキュリティ ポリシーの管理に使用する .NET Framework ツールについて説明します。  
  
 [セキュリティで保護されたアプリケーションを作成するためのリソース](http://msdn.microsoft.com/en-us/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 安全なアプリケーションを作成するためのトピックへのリンク集です。  
  
 [セキュリティ参考文献](/visualstudio/ide/security-bibliography)  
 オンラインまたは出版物として提供されている外部リソースへのリンク集です。  
  
## <a name="see-also"></a>参照  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
