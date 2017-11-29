---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1ff00bead6130601070ac94686ee9622a6fe218
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="findprivatekey"></a>FindPrivateKey
証明書ストア内の特定の X.509 証明書に関連付けられている秘密キー ファイルの場所と名前を見つけることが困難な場合があります。 FindPrivateKey.exe ツールを使用すると、この処理を容易に実行できます。  
  
> [!IMPORTANT]
>  FindPrivateKey は、使用する前にコンパイルする必要があるサンプルです。 FindPrivateKey ツールを構築する方法の FindPrivateKey プロジェクトをビルドするには"するには"以下のセクションの手順を参照してください。  
  
 X.509 証明書は、コンピューターの管理者または任意のユーザーによってインストールされます。 ただし、証明書は別のアカウント ([!INCLUDE[wxp](../../../../includes/wxp-md.md)] の ASPNET、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] の NETWORK SERVICE アカウントなど) で実行されているサービスからアクセスすることができます。  
  
 別のアカウントでは、秘密キー ファイルへアクセスできない場合があります。これは、証明書が最初にこのアカウントによってインストールされていないからです。 FindPrivateKey ツールでは、指定された X.509 証明書の秘密キー ファイルの場所を検索できます。 特定の X.509 証明書の秘密キー ファイルの場所がわかれば、このファイルに対するアクセス許可の追加または削除を実行できます。  
  
 セキュリティ用の証明書を使用するこのサンプルでは、Setup.bat ファイル内の FindPrivateKey ツールを使用します。 秘密キー ファイルが見つかったら、Cacls.exe などの別のツールを使用して、このファイルに対する適切なアクセス権を設定できます。  
  
 自己ホスト型の実行可能ファイルなどの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをユーザー アカウントで実行している場合は、そのユーザー アカウントがそのファイルへの読み取り専用のアクセス権限を持っていることを確認します。 インターネット インフォメーション サービス (IIS) で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを実行している場合、サービスが実行されている既定のアカウントは、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] では ASPNET、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では NETWORK SERVICE です。これらのアカウントには、既定では秘密キー ファイルへのアクセス権限がありません。  
  
## <a name="examples"></a>例  
 証明書にアクセスする際、プロセスにその証明書に対する読み取り権限がない場合、次の例のような例外メッセージが表示されます。  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 この例外が発生したら、FindPrivateKey ツールを使用して秘密キー ファイルを検索し、サービスが実行されているプロセスにアクセス権を設定します。 たとえば、次の例に示すように、Cacls.exe ツールを使用して処理できます。  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a>FindPrivateKey プロジェクトをビルドするには  
  
1.  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]を開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。  
  
2.  .sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。  
  
3.  **ビルド**メニューの **ソリューションのリビルド**です。 クライアント プログラムが client\bin にビルドされ、サービス プログラムが service\bin にビルドされます。  
  
4.  ソリューションをビルドすると、FindPrivateKey.exe ファイルが生成されます。  
  
## <a name="conventionscommand-line-entries"></a>規則 - コマンド ラインのエントリ  
 "[*オプション*]"オプションのパラメーターのセットを表します。  
  
 "{*オプション*}"必須のパラメーターのセットを表します。  
  
 "*option1* &#124;です。*・ オプション 2*"オプションのセットのいずれかを表します。  
  
 "\<*値*>"を入力するパラメーター値を表します。  
  
## <a name="usage"></a>使用方法  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 指定項目:  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 コマンド プロンプトでパラメーターを指定しない場合、このヘルプ テキストが表示されます。  
  
## <a name="examples"></a>例  
 この例では、現在のユーザーの Personal ストアで、"CN=localhost" というサブジェクト名を持つ証明書のファイル名を検索します (FindPrivateKey My CurrentUser -n "CN=localhost")。  
  
 この例では、現在のユーザーの Personal ストアで、"CN=localhost" というサブジェクト名を持つ証明書のファイル名を検索し、ディレクトリの完全パスを出力します。  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 この例では、ローカル コンピューターの Personal ストアで、"03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" というサムプリントを持つ証明書のファイル名を検索します。  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a>関連項目
