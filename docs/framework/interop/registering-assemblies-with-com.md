---
title: "COM へのアセンブリの登録 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM 相互運用機能, 登録 (アセンブリを)"
  - "相互運用 (アンマネージ コードとの), 登録 (アセンブリを)"
  - "登録 (アセンブリを)"
  - "登録解除 (アセンブリの)"
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# COM へのアセンブリの登録
[アセンブリ登録ツール \(Regasm.exe\)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) と呼ばれるコマンド ライン ツールを実行して、COM で使用するアセンブリを登録または登録解除できます。  Regasm.exe はシステム レジストリにクラスの情報を追加するので、COM クライアントが .NET Framework クラスを透過的に使用できます。  <xref:System.Runtime.InteropServices.RegistrationServices> クラスは、これと同等の機能を提供します。  
  
 マネージ コンポーネントを COM クライアントからアクティブにするには、Windows レジストリに登録する必要があります。  Regasm.exe によって通常 Windows レジストリに追加されるキーを次の表に示します  \(000000 は実際の GUID 値を示します\)。  
  
|GUID|説明|レジストリ キー|  
|----------|--------|--------------|  
|CLSID|クラス ID|HKEY\_CLASSES\_ROOT\\CLSID\\{000...000}|  
|IID|インターフェイス ID|HKEY\_CLASSES\_ROOT\\Interface\\{000...000}|  
|LIBID|ライブラリ ID|HKEY\_CLASSES\_ROOT\\TypeLib\\{000...000}|  
|\[ProgID\]|プログラム ID|HKEY\_CLASSES\_ROOT\\000...000|  
  
 HKCR\\CLSID\\{0000...0000} キーの下には、既定値としてそのクラスの ProgID が設定され、Class と Assembly という 2 つの名前付きの値が新しく追加されます。  ランタイムは、レジストリから Assembly の値を読み取り、その値をランタイムのアセンブリ リゾルバーに渡します。  アセンブリ リゾルバーは、名前やバージョン番号などのアセンブリ情報に基づいて、そのアセンブリを検索します。  アセンブリ リゾルバーでアセンブリを検出するには、アセンブリが次のいずれかの場所に存在している必要があります。  
  
-   グローバル アセンブリ キャッシュ \(厳密な名前を持つアセンブリである必要があります\)。  
  
-   アプリケーション ディレクトリ。  アプリケーション パスから読み込まれたアセンブリは、そのアプリケーションからしかアクセスできません。  
  
-   Regasm.exe に対して **\/codebase** オプションで指定したファイル パス。  
  
 Regasm.exe は HKCR\\CLSID\\{0000....0000} キーの下に、InProcServer32 キーも作成します。  このキーの既定値は、共通言語ランタイム \(Mscoree.dll\) を初期化する DLL の名前に設定されます。  
  
## レジストリ エントリのチェック  
 COM 相互運用機能では、.NET Framework クラスのインスタンスを生成するために、標準のクラス ファクトリの実装が用意されています。  クライアントでは、他の COM コンポーネントの場合と同様に、マネージ DLL 上の **DllGetClassObject** を呼び出してクラス ファクトリを取得し、オブジェクトを生成できます。  
  
 `InprocServer32` のサブキーのために、共通言語ランタイムがマネージ オブジェクトが作成されることを示す、Mscoree.dll への参照は、従来の COM タイプ ライブラリの代わりに似ています。  
  
## 参照  
 [COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [方法: COM から .NET 型を参照する](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)   
 [Calling a .NET Object](http://msdn.microsoft.com/ja-jp/40c9626c-aea6-4bad-b8f0-c1de462efd33)   
 [Deploying an Application for COM Access](http://msdn.microsoft.com/ja-jp/fb63564c-c1b9-4655-a094-a235625882ce)