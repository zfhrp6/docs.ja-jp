---
title: "XML シリアライザー ジェネレーター ツール (Sgen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73669fcfd74f9c4948c8ec976ff3271c72f1033a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>XML シリアライザー ジェネレーター ツール (Sgen.exe)
XML シリアライザー ジェネレーターは、指定された型のオブジェクトをシリアル化または逆シリアル化するとき、<xref:System.Xml.Serialization.XmlSerializer> の起動パフォーマンスを向上させるために、指定されたアセンブリの型に対して XML シリアル化アセンブリを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|オプション|説明|  
|------------|-----------------|  
|**/a****[ssembly]****:***filename*|アセンブリ、または *filename* によって指定される実行可能ファイルに含まれるすべての型に対して、シリアル化コードを生成します。 指定できるファイル名は 1 つのみです。 この引数を複数指定した場合は、最後のファイル名が使用されます。|  
|**/c[ompiler]:** *options*|オプションを C# コンパイラに渡すように指定します。 csc.exe のすべてのオプションがサポートされ、コンパイラに渡されます。 このオプションを使用して、アセンブリに署名してキー ファイルを指定するように指定できます。|  
|**/d****[ebug]**|デバッガーで使用できるイメージを生成します。|  
|**/f[orce]**|同じ名前の既存のアセンブリに上書きします。 既定値は **false** です。|  
|**/help または /?**|このツールのコマンド構文とオプションを表示します。|  
|**/k****[eep]**|生成されたソース ファイルとその他の一時ファイルをシリアル化アセンブリにコンパイルした後、元のファイルを削除しません。 このオプションを使用して、ツールが特定の型に対してシリアル化コードを生成するかどうかを指定できます。|  
|**/n****[ologo]**|Microsoft の著作権情報を表示しません。|  
|**/o****[ut]****:***path*|生成されたアセンブリの保存先のディレクトリを指定します。 **注:** 生成されたアセンブリの名前は、入力アセンブリの名前と "xmlSerializers.dll" で構成されます。|  
|**/p****[roxytypes]**|XML Web サービス プロキシ型に対してのみシリアル化コードを生成します。|  
|**/r****[eference]****:***assemblyfiles*|XML シリアル化が必要な型によって参照されるアセンブリを指定します。 コンマで区切られた複数のアセンブリ ファイルを受け入れます。|  
|**/s****[ilent]**|成功メッセージを表示しません。|  
|**/t****[ype]****:***type*|指定された型に対してのみ、シリアル化コードを生成します。|  
|**/v****[erbose]**|デバッグに関する詳細出力を表示します。 <xref:System.Xml.Serialization.XmlSerializer> でシリアル化できない対象アセンブリの型を一覧表示します。|  
|**/?**|このツールのコマンド構文とオプションを表示します。|  
  
## <a name="remarks"></a>コメント  
 XML シリアライザー ジェネレーターを使用しない場合、<xref:System.Xml.Serialization.XmlSerializer> はアプリケーションを実行するたびに、各型に対してシリアル化コードとシリアル化アセンブリを生成します。 XML シリアル化起動のパフォーマンスを向上させるには、Sgen.exe ツールを使用して、あらかじめこれらのアセンブリを生成します。 生成したアセンブリは、アプリケーションで配置できます。  
  
 XML シリアライザー ジェネレーターは、サーバーとの通信に XML Web サービス プロキシを使用するクライアントのパフォーマンスも向上させますが、これは型が初めて読み込まれるとき、シリアル化プロセスによってパフォーマンスが低下しないためです。  
  
 これらの生成されたアセンブリは、Web サービスのサーバー側では使用できません。 このツールは、Web サービス クライアントと手動シリアル化シナリオに対してのみ使用できます。  
  
 シリアル化する型を含むアセンブリの名前が MyType.dll の場合、関連するシリアル化アセンブリの名前は MyType.XmlSerializers.dll となります。  
  
## <a name="examples"></a>例  
 次のコマンドは、Data.dll という名前のアセンブリに含まれるすべての型をシリアル化するために、Data.XmlSerializers.dll という名前のアセンブリを作成します。  
  
```  
sgen Data.dll   
```  
  
 Data.XmlSerializers.dll アセンブリは、Data.dll の型をシリアル化および逆シリアル化する必要のあるコードから参照できます。  
  
## <a name="see-also"></a>関連項目  
 [ツール](../../../docs/framework/tools/index.md)  
 [XML Web サービスの概要](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
 [コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
