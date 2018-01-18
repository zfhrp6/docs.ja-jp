---
title: "REF CURSOR の例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c9d282aba600d2475594887844ef19fc8eea374f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="ref-cursor-examples"></a>REF CURSOR の例
REF CURSOR の例は、REF CURSOR の使い方を説明する、次の 3 つの Microsoft Visual Basic の例によって構成されています。  
  
|サンプル|説明|  
|------------|-----------------|  
|[OracleDataReader の REF CURSOR パラメーター](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|この例では、REF CURSOR パラメーターを返し、<xref:System.Data.OracleClient.OracleDataReader> として値を読み込む PL/SQL ストアド プロシージャを実行します。|  
|[OracleDataReader を使用した複数の REF CURSOR からのデータの取得](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|この例は、2 つの REF CURSOR パラメーターを返しを使用して値を読み取る、PL/SQL ストアド プロシージャを実行、 **OracleDataReader**です。|  
|[1 つまたは複数の REF CURSOR を使用した DataSet の値の設定](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|この例では、2 つの REF CURSOR パラメーターを返し、返された行を <xref:System.Data.DataSet> に入力する PL/SQL ストアド プロシージャを実行します。|  
  
 これらの例を使用するには、必要に応じて Oracle テーブルを作成し、さらに PL/SQL パッケージとパッケージ本体を作成する必要があります。  
  
## <a name="creating-the-oracle-tables"></a>Oracle テーブルの作成  
 これらの例では、Oracle Scott/Tiger スキーマで定義されたテーブルを使用します。 Oracle Scott/Tiger スキーマは、ほとんどの Oracle のインストールに含まれています。 このスキーマが含まれていない場合は、{OracleHome}\rdbms\admin\scott.sql にある SQL コマンド ファイルを使用して、これらの例で使用されているテーブルとインデックスを作成します。  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Oracle パッケージとパッケージ本体の作成  
 これらの例では、次の PL/SQL パッケージとパッケージ本体がサーバー上に必要になります。 次の Oracle パッケージを Oracle サーバー上に作成します。  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 Oracle サーバーで、次の Oracle パッケージ本体を作成します。  
  
```  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS   
        V_CURSOR T_CURSOR;   
    BEGIN   
        IF N_EMPNO <> 0   
        THEN  
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO   
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE   
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;   
    END OPEN_ONE_CURSOR;   
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS   
        V_CURSOR1 T_CURSOR;   
        V_CURSOR2 T_CURSOR;   
    BEGIN   
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;   
        DEPTCURSOR := V_CURSOR2;   
    END OPEN_TWO_CURSORS;   
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a>参照  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
