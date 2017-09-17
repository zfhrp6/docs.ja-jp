---
title: "COM へのアセンブリの登録"
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
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a467bff903701cf252da983e1265c679171e90b0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="registering-assemblies-with-com"></a>COM へのアセンブリの登録
[アセンブリ登録ツール (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) というコマンドライン ツールを実行して、COM で使うアセンブリを登録または登録解除できます。 Regasm.exe は、COM クライアントが .NET Framework のクラスを透過的に使うことができるように、クラスについての情報をシステム レジストリに追加します。 <xref:System.Runtime.InteropServices.RegistrationServices> クラスには、同等の機能が用意されています。  
  
 マネージ コンポーネントを COM クライアントからアクティブ化するには、先にマネージ コンポーネントを Windows レジストリに登録しておく必要があります。 次の表では、Regasm.exe が通常、Windows レジストリに追加するキーを示します  (000000 は実際の GUID の値を示します)。  
  
|GUID|説明|レジストリ キー|  
|----------|-----------------|------------------|  
|CLSID|クラス識別子|HKEY_CLASSES_ROOT\CLSID\\{000…000}|  
|IID|インターフェイス識別子|HKEY_CLASSES_ROOT\Interface\\{000…000}|  
|LIBID|ライブラリ識別子|HKEY_CLASSES_ROOT\TypeLib\\{000…000}|  
|ProgID|プログラム識別子|HKEY_CLASSES_ROOT\000…000|  
  
 HKCR\CLSID\\{0000…0000} キーの下では、既定値がクラスの ProgID に設定され、Class と Assembly という 2 つの新しい名前付きの値が追加されます。 ランタイムは、レジストリから Assembly の値を読み取り、ランタイム アセンブリ リゾルバーに渡します。 アセンブリ リゾルバーは、名前やバージョン番号などのアセンブリの情報に基づいて、アセンブリの特定を試みます。 アセンブリ リゾルバーがアセンブリを特定するには、アセンブリが次のいずれかの場所に存在する必要があります。  
  
-   グローバル アセンブリ キャッシュ (厳密な名前付きアセンブリである必要があります)。  
  
-   アプリケーション ディレクトリ内。 アプリケーション パスから読み込まれたアセンブリは、そのアプリケーションからのみアクセスできます。  
  
-   Regasm.exe に対する **/codebase** オプションで指定されたファイル パス上。  
  
 Regasm.exe は、HKCR\CLSID\\{0000…0000} キーの下に InProcServer32 キーも作成します。 このキーの既定値は、共通言語ランタイム (Mscoree.dll) を初期化する DLL の名前に設定されます。  
  
## <a name="examining-registry-entries"></a>レジストリ エントリを調べる  
 COM 相互運用は、.NET Framework クラスのインスタンスを作成するための標準のクラス ファクトリの実装を提供します。 クライアントは、他の COM コンポーネントと同様に、マネージ DLL で **DllGetClassObject** を呼び出してクラス ファクトリを取得し、オブジェクトを作成することができます。  
  
 `InprocServer32` サブキーには、従来の COM タイプ ライブラリの代わりに Mscoree.dll への参照が表示され、共通言語ランタイムがマネージ オブジェクトを作成することを示します。  
  
## <a name="see-also"></a>関連項目  
 [COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [方法: COM から .NET 型を参照する](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)   
 [.NET オブジェクトの呼び出し](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)   
 [COM アクセスに対するアプリケーションの配置](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)

