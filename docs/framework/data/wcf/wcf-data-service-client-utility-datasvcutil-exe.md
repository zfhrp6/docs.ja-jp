---
title: WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 3206947d06a1736116674b70e469c20f8f4fca86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364527"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe)
DataSvcUtil.exe は、コマンド ライン ツールによって提供される[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]を消費する、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードし、.NET Framework クライアント アプリケーションからデータ サービスにアクセスするために必要なクライアント データ サービス クラスが生成されます。 このユーティリティでは、以下のメタデータ ソースを使用してデータ クラスを生成できます。  
  
-   データ サービスのルート URI。 ユーティリティは、データ サービスによって公開されるデータ モデルが記述されたサービス メタデータ ドキュメントを要求します。 詳細については、次を参照してください。 [OData: サービス メタデータ ドキュメント](http://go.microsoft.com/fwlink/?LinkId=186070)です。  
  
-   定義されている、概念スキーマ定義言語 (CSDL) を使用して定義されているデータ モデル ファイル (.csdl)、 [ \[MC-CSDL\]: 概念スキーマ定義ファイル形式](http://go.microsoft.com/fwlink/?LinkID=159072)仕様です。  
  
-   Entity Framework に付属する Entity Data Model ツールを使用して作成された .edmx ファイル。 詳細については、次を参照してください。、 [ \[MC-EDMX\]: データ サービスのパッケージ形式の Entity Data Model](http://go.microsoft.com/fwlink/?LinkID=178833)仕様です。  
  
 詳細については、次を参照してください。[する方法: 手動で生成クライアント データ サービス クラス](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)です。  
  
 DataSvcUtil.exe ツールは [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ディレクトリにインストールされます。 多くの場合、C:\Windows\Microsoft.NET\Framework\v4.0 にあります。 64 ビット システムの場合は、C:\Windows\Microsoft.NET\Framework64\v4.0 にあります。 Visual Studio コマンド プロンプトから DataSvcUtil.exe ツールをアクセスすることもできます (をクリックして**開始**、 をポイント**すべてのプログラム**、 をポイント**Microsoft Visual Studio 2010**、をポイント**Visual Studio Tools**、クリックして**Visual Studio 2010 コマンド プロンプト**)。  
  
## <a name="syntax"></a>構文  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|オプション|説明|  
|------------|-----------------|  
|`/dataservicecollection`|オブジェクトをコントロールにバインドするために必要なコードも生成することを指定します。|  
|`/help`<br /><br /> または<br /><br /> `/?`|このツールのコマンド構文とオプションを表示します。|  
|`/in:` *\<ファイル >*|.csdl ファイルまたは .edmx ファイル、またはファイルがあるディレクトリを指定します。|  
|`/language:`[VB&#124;CSharp]|生成されるソース コード ファイルの言語を指定します。 既定の言語は C# です。|  
|`/nologo`|著作権メッセージが表示されないようにします。|  
|`/out:` *\<ファイル >*|生成されたクライアント データ サービス クラスを含むソース コード ファイルの名前を指定します。|  
|`/uri:` *\<文字列 >*|URI、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。|  
|`/version:`[1.0&#124;2.0]|許容される [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の最上位バージョンを指定します。 基に、バージョンが決定されます、`DataServiceVersion`返されたデータ サービス メタデータの DataService 要素の属性です。 詳細については、次を参照してください。[データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)です。 指定すると、`/dataservicecollection`パラメーターも指定してください`/version:2.0`データ バインディングを有効にします。|  
  
## <a name="see-also"></a>関連項目  
 [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [方法: データ サービス参照を追加する](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
