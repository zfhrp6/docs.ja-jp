---
title: "安全なクライアント アプリケーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1218cda46a6a901c3dbf9fb11333b04d0133df42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="secure-client-applications"></a>安全なクライアント アプリケーション
通常、アプリケーションは多数の要素で構成されており、それぞれをデータの損失やシステムのセキュリティ侵害を招く脆弱性から確実に保護する必要があります。 安全なユーザー インターフェイスを作成し、攻撃者によるデータやシステム リソースへのアクセスを未然に阻止することで、多くの問題を防ぐことができます。  
  
## <a name="validate-user-input"></a>ユーザー入力の検証  
 データにアクセスするアプリケーションを構築する場合、ユーザーの入力はすべて悪意のあるものと想定しない限り、 攻撃に対する脆弱性をアプリケーションから取り除くことはできません。 .NET Framework には、入力できる文字数の制限など、入力コントロールの値の範囲を設定するクラスが用意されています。 イベントを捕捉することによって、値の有効性を確認するプロシージャを作成できます。 ユーザーによって入力されるデータを検証し、厳密に型指定することで、アプリケーションをスクリプト インジェクションや SQL インジェクションなどの攻撃にさらす機会を制限できます。  
  
> [!IMPORTANT]
>  クライアント アプリケーションだけでなく、データ ソース側でもユーザー入力を検証する必要があります。 攻撃者がアプリケーションを迂回し、データ ソースを直接攻撃してくる可能性もあります。  
  
 [セキュリティとユーザー入力](../../../../docs/standard/security/security-and-user-input.md)  
 発見が難しく大きな危険を招く可能性のあるユーザー入力に関連したバグへの対処方法を説明します。  
  
 [ASP.NET Web ページで、ユーザー入力の検証](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 ASP.NET の検証コントロールを使ったユーザー入力の検証について概要を説明します。  
  
 [Windows フォームでのユーザー入力](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Windows フォーム アプリケーションにおけるマウス入力およびキーボード入力の検証に関連したリンクや情報を提供します。  
  
 [.NET Framework 正規表現](../../../../docs/standard/base-types/regular-expressions.md)  
 <xref:System.Text.RegularExpressions.Regex> クラスを使用してユーザー入力の有効性を確認する方法について説明します。  
  
## <a name="windows-applications"></a>Windows アプリケーション  
 これまで、Windows アプリケーションは、アクセスがすべて許可された状態で実行されていました。 .NET Framework は、コード アクセス セキュリティ (CAS) を使用して Windows アプリケーションで実行されるコードを制限するインフラストラクチャを提供します。 ただし、CAS だけでは、アプリケーションを保護するには不十分です。  
  
 [Windows フォームのセキュリティ](../../../../docs/framework/winforms/windows-forms-security.md)  
 Windows フォーム アプリケーションをセキュリティで保護する方法について説明します。また、関連項目へのリンクがあります。  
  
 [Windows フォームとアンマネージ アプリケーション](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Windows フォーム アプリケーションでアンマネージ アプリケーションと対話する方法について説明します。  
  
 [ClickOnce 配置の Windows フォーム アプリケーション](http://msdn.microsoft.com/en-us/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Windows フォーム アプリケーションでの `ClickOnce` 配置の使用方法およびセキュリティへの影響について説明します。  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET と XML Web サービス  
 通常、ASP.NET アプリケーションは、アクセスを Web サイトの一部に制限し、データ保護およびサイト セキュリティのための他のメカニズムを提供する必要があります。 以下のリンクにアクセスすると、ASP.NET アプリケーションをセキュリティで保護するための有益な情報を見つけることができます。  
  
 XML Web サービスは、ASP.NET アプリケーション、Windows フォーム アプリケーション、またはその他の Web サービスが使用できるデータを提供します。 クライアント アプリケーションのセキュリティだけでなく、Web サービスそのもののセキュリティを管理する必要があります。  
  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[NIB: ASP.NET のセキュリティ](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d)|ASP.NET アプリケーションをセキュリティで保護する方法について説明します。|  
|[ASP.NET を使用して作成された XML Web サービスをセキュリティで保護します。](http://msdn.microsoft.com/en-us/354b2ab1-2782-4542-b32a-dc560178b90c)|ASP.NET Web サービスへのセキュリティの実装方法について説明します。|  
|[スクリプトによる攻略の概要](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Web ページに悪意のある文字の挿入を試みるスクリプト攻略攻撃を阻止する方法について説明します。|  
|[NIB: Basic ASP.NET Web アプリケーションのセキュリティのプラクティス](http://msdn.microsoft.com/en-us/94a52ab8-731d-417e-b997-721baf43df38)|一般的なセキュリティ情報のほか、より詳細なページへのリンクも掲載されています。|  
  
## <a name="remoting"></a>リモート処理  
 .NET リモート処理を使用すると、広範囲の分散アプリケーションを簡単に構築できます。その場合、アプリケーションのコンポーネントを、すべて 1 台のコンピューターに置くことも、遠隔地のコンピューターに分散させることもできます。 同じコンピューター上、またはネットワークを経由してアクセスできる他の任意のコンピューター上にある他のプロセスのオブジェクトを使用するクライアント アプリケーションを構築できます。 また、.NET リモート処理を使用すると、同じプロセスの他のアプリケーション ドメインと通信できます。  
  
|リソース|説明|  
|--------------|-----------------|  
|[リモート アプリケーションの構成](http://msdn.microsoft.com/en-us/92c0c097-d984-4315-835b-7490ecdf1097)|一般的な問題を回避するためのリモート処理アプリケーションの構成方法について説明します。|  
|[リモート処理でのセキュリティ](http://msdn.microsoft.com/en-us/9574262c-d4b1-41c5-8600-24ff147c0add)|認証と暗号化のほか、リモート処理に関連したその他のセキュリティ トピックについて説明します。|  
|[セキュリティとリモート処理の考慮事項](../../../../docs/framework/misc/security-and-remoting-considerations.md)|保護されたオブジェクトやアプリケーション ドメインの境界越えに伴うセキュリティの問題について説明します。|  
  
## <a name="see-also"></a>参照  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [データ アクセスに関する推奨事項](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [アプリケーションの保護](/visualstudio/ide/securing-applications)  
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
