---
title: COM へのアセンブリの登録
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92f36488dec113dcffffac3e6cdc0c26a690b5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389162"
---
# <a name="registering-assemblies-with-com"></a>COM へのアセンブリの登録
[アセンブリ登録ツール (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) というコマンドライン ツールを実行して、COM で使うアセンブリを登録または登録解除できます。 Regasm.exe は、COM クライアントが .NET Framework のクラスを透過的に使うことができるように、クラスについての情報をシステム レジストリに追加します。 <xref:System.Runtime.InteropServices.RegistrationServices> クラスには、同等の機能が用意されています。  
  
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
  
## <a name="see-also"></a>参照  
 [COM への .NET Framework コンポーネントの公開](exposing-dotnet-components-to-com.md)  
 [方法: COM から .NET 型を参照する](how-to-reference-net-types-from-com.md)  
 [.NET オブジェクトの呼び出し](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))  
 [COM アクセスに対するアプリケーションの配置](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))
