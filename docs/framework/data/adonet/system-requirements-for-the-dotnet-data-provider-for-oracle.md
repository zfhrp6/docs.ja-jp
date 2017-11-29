---
title: ".NET Framework Data Provider for Oracle のシステム要件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 84bf37dfadf038bc418fc8c2c6746baa58d717b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>.NET Framework Data Provider for Oracle のシステム要件
.NET Framework Data Provider for Oracle を使用するには、MDAC (Microsoft Data Access Components) のバージョン 2.6 以降が必要です。 MDAC 2.8 SP1 をインストールすることをお勧めします。  
  
 Oracle 8i Release 3 (8.1.7) Client 以降もインストールする必要があります。  
  
 UTF16 は Oracle 9i の新機能なので、Oracle 9i 以前のバージョンの Oracle Client ソフトウェアでは UTF16 データベースにアクセスできません。 この機能を使用するには、お使いのクライアント ソフトウェアを Oracle 9i 以降にアップグレードする必要があります。  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Data Provider for Oracle と Unicode データの使用  
 .NET Framework Data Provider for Oracle および Oracle クライアント ライブラリを使用するときに考慮が必要な、Unicode に関連する問題の一覧を以下に示します。 詳細については、Oracle のドキュメントを参照してください。  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>接続文字列の属性に Unicode 値を設定する  
 Oracle を操作する場合、接続文字列の属性を使用し、  
  
```  
Unicode=True   
```  
  
 UTF-16 モードで Oracle クライアント ライブラリを初期化することができます。 これにより、Oracle クライアント ライブラリで、マルチバイト文字列の代わりに UTF-16 (UCS-2 とよく似ています) が使用できるようになります。 新たに変換作業を行わなくても、Data Provider for Oracle で Oracle のコード ページを常に使用できます。 この構成は、Oracle 9i クライアントを使用して、AL16UTF16 の代替文字セットを持つ Oracle 9i データベースと通信する場合に動作します。 その他のリソースが、Unicode に変換するために必要な Oracle 9i クライアントが Oracle 9i サーバーと通信を行うとき**CommandText**を適切なマルチ バイト文字の値を設定する 9i サーバーが使用されます。 安全な構成が確保されていることがわかっている場合は、`Unicode=True` を接続文字列に追加することにより回避することができます。  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Oracle クライアントと Oracle サーバーのバージョンの混在  
 Oracle 8i クライアントがアクセスできない**NCHAR**、 **NVARCHAR2**、または**NCLOB**サーバーの各国語文字セットが AL16UTF16 として指定されている場合、Oracle 9i データベース内のデータ (既定の設定を Oracle 9i)。 UTF-16 文字セットのサポートは Oracle 9i まで導入されなかったため、Oracle 8i クライアントでは読み取れません。  
  
### <a name="working-with-utf-8-data"></a>UTF-8 データの使用  
 代替文字セットを設定するには、レジストリ キー HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG を UTF8 に設定します。 詳細については、ご使用のプラットフォームに関する Oracle のインストール ノートを参照してください。 既定の設定は、Oracle Client ソフトウェアのインストールに使用する言語の基本文字セットになっています。 接続するデータベースの各国語文字セットと言語が一致するように設定されていないと、パラメーターと列の組み合わせは、各国語文字セットではなくプライマリ データベースの文字セットでデータを送受信します。  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob で更新できるのは Full 文字列のみです。  
 ユーザビリティ上の理由から、<xref:System.Data.OracleClient.OracleLob>オブジェクトは、.NET Framework Stream クラスから継承し、提供**ReadByte**と**WriteByte**メソッドです。 メソッドも実装など**CopyTo**と**消去**その、Oracle のセクションで動作**LOB**オブジェクト。 Oracle クライアント ソフトウェアが多数の文字を使用する Api を提供する一方、 **LOB**s (**CLOB**と**NCLOB**)。 ただし、これらの API は full 文字列でのみ動作します。 Data Provider for Oracle がサポートを実装するこの違いにより、**読み取り**と**ReadByte**バイトの方法で utf-16 データを操作します。 ただし、他の方法、 **OracleLob**オブジェクトは full 文字列操作のみを許可します。  
  
## <a name="see-also"></a>関連項目  
 [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
