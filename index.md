 <%@ page contentType="text/html; charset=utf-8"%>
 <%@ include file="/comm/jsp/includes.jsp"%>
 <!DOCTYPE>
 <html>
    <head>
        <title>查詢他行票核心流水更新</title>
        <%@ include file="/comm/jsp/header.jsp"%>
        <script type="text/javascript">
        
$(document).ready(function(){
    grid1 = $('#L').newgrid({
        pages : '${d["PAGES"]}',
        page : '${d["PAGE"]}',
        buttons : [
                  		{caption : msgs.gridBtnDownLoad,bclass:'download', onpress:downloadData}
                  ]
    });
function downloadData(){
        var listData = grid1.getAllData();
        $.assign({"listData":listData});
        $.nextPage({
                    url : "<c:url value="/xds?targetUri=service.ibscore.excelToTxtService"/>",
                   form : "form1",
                   data : {
                           method : "download",
                           flag   : "transient"
                   }
        });
        Ext.MessageBox.hide();
    }    
  });

         document.onkeydown = initHotKey;
        </script>
        <%@ include file="/comm/jsp/bodyTop.jsp"%>
        <form name='form1' id='form1' method='post' action='<c:url value="/xds?targetUri=service.ibscore.ibscoreService"/>&flag=${flag}'>
            <div name='panel1' id='panel1' class='panel'>
                <table class='tableLayout' border='0' cellspacing='0' cellpadding='0'>
                    <thead>
                        <th style='width:20PX'/>
                        <th style='width:150PX'/>
                        <th style='width:20PX'/>
                        <th style='width:150PX'/>
                        <th style='width:20PX'/>
                        <th style='width:200PX'/>
                    </thead>
                    <tr name='row1' id='row1'>
                        <td colspan='6'>
                            
                                <table  name='L' id='L' height='400' width='1094' border='0' style='display:none' cellspacing='0' cellpadding='0'>
                                    <thead>
<tr>
                                        <th name='UPD_DT' width='70' >更新日期</th>
                                        <th name='BATNO' width='70' >批次號</th>
                                        <th name='BAT_SEQ' width='70' >批次內順序號</th>
                                        <th name='DEP_DT' width='70' >存入日期</th>
                                        <th name='BK' width='100'  alias='{<c:forEach items="${options['AMCM_BK_01'].options}" var="item" varStatus="itemStatus">"${item.value}":"${item.value} - <branch:language key="AMCM_BK_01.${item.value}" />"<c:if test="${itemStatus.count < fn:length(options['AMCM_BK_01'].options)}">,</c:if></c:forEach>}' >銀行號</th>
                                        <th name='BIL_TYP' width='70'  alias='{<c:forEach items="${options['BC_BITP_01'].options}" var="item" varStatus="itemStatus">"${item.value}":"${item.value} - <branch:language key="BC_BITP_01.${item.value}" />"<c:if test="${itemStatus.count < fn:length(options['BC_BITP_01'].options)}">,</c:if></c:forEach>}' >票據類型</th>
                                        <th name='SEQ' width='70' >順序號</th>
                                        <th name='BIL_NO' width='150' >票據號</th>
                                        <th name='BIL_CCY' width='100'  alias='{<c:forEach items="${options['CCY_08'].options}" var="item" varStatus="itemStatus">"${item.value}":"${item.value} - <branch:language key="CCY_08.${item.value}" />"<c:if test="${itemStatus.count < fn:length(options['CCY_08'].options)}">,</c:if></c:forEach>}' >票據幣別</th>
                                        <th name='BIL_AMT' width='100' >票據金額</th>
                                        <th name='DEP_IND' width='100'  alias='{<c:forEach items="${options['FLG_258'].options}" var="item" varStatus="itemStatus">"${item.value}":"${item.value} - <branch:language key="FLG_258.${item.value}" />"<c:if test="${itemStatus.count < fn:length(options['FLG_258'].options)}">,</c:if></c:forEach>}' >即時存入標識</th>
                                        <th name='NO_FLG' width='70'  alias='{<c:forEach items="${options['FLG_201'].options}" var="item" varStatus="itemStatus">"${item.value}":"${item.value} - <branch:language key="FLG_201.${item.value}" />"<c:if test="${itemStatus.count < fn:length(options['FLG_201'].options)}">,</c:if></c:forEach>}' >正常逾時票標</th>
                                        <th name='RET_STATUS' width='70'  alias='{<c:forEach items="${options['FLG_279'].options}" var="item" varStatus="itemStatus">"${item.value}":"${item.value} - <branch:language key="FLG_279.${item.value}" />"<c:if test="${itemStatus.count < fn:length(options['FLG_279'].options)}">,</c:if></c:forEach>}' >更新狀態</th>
                                        <th name='REASON' width='70' >失敗原因</th>
                                    </tr>
</thead>
                                    <tbody>
                                        <tr class='template' style='display:none;'>
                                            <td value="" >{UPD_DT}&nbsp;</td>
                                            <td value="" >{BATNO}&nbsp;</td>
                                            <td value="" >{BAT_SEQ}&nbsp;</td>
                                            <td value="" >{DEP_DT}&nbsp;</td>
                                            <td value="" >{BK}&nbsp;</td>
                                            <td value="" >{BIL_TYP}&nbsp;</td>
                                            <td value="" >{SEQ}&nbsp;</td>
                                            <td value="" >{BIL_NO}&nbsp;</td>
                                            <td value="" >{BIL_CCY}&nbsp;</td>
                                            <td value="" >{BIL_AMT}&nbsp;</td>
                                            <td value="" >{DEP_IND}&nbsp;</td>
                                            <td value="" >{NO_FLG}&nbsp;</td>
                                            <td value="" >{RET_STATUS}&nbsp;</td>
                                            <td value="" >{REASON}&nbsp;</td>
                                        </tr>
                                        <c:forEach items="${d['L']}"  var="item">
                                            <tr>
                                                <td value="${item.map['UPD_DT']}" >${item.map['UPD_DT']}&nbsp;</td>
                                                <td value="${item.map['BATNO']}" >${item.map['BATNO']}&nbsp;</td>
                                                <td value="${item.map['BAT_SEQ']}" >${item.map['BAT_SEQ']}&nbsp;</td>
                                                <td value="${item.map['DEP_DT']}" >${item.map['DEP_DT']}&nbsp;</td>
                                                <td value="${item.map['BK']}" >${item.map['BK']}&nbsp;</td>
                                                <td value="${item.map['BIL_TYP']}" >${item.map['BIL_TYP']}&nbsp;</td>
                                                <td value="${item.map['SEQ']}" >${item.map['SEQ']}&nbsp;</td>
                                                <td value="${item.map['BIL_NO']}" >${item.map['BIL_NO']}&nbsp;</td>
                                                <td value="${item.map['BIL_CCY']}" >${item.map['BIL_CCY']}&nbsp;</td>
                                                <td value="${item.map['BIL_AMT']}" >${item.map['BIL_AMT']}&nbsp;</td>
                                                <td value="${item.map['DEP_IND']}" >${item.map['DEP_IND']}&nbsp;</td>
                                                <td value="${item.map['NO_FLG']}" >${item.map['NO_FLG']}&nbsp;</td>
                                                <td value="${item.map['RET_STATUS']}" >${item.map['RET_STATUS']}&nbsp;</td>
                                                <td value="${item.map['REASON']}" >${item.map['REASON']}&nbsp;</td>
                                            </tr>
                                        </c:forEach>
                                    </tbody>
                                </table>
                        </td>
                    </tr>
                </table>
            </div>
            <div name='panel2' id='panel2' class='panel'>
                <input type='hidden' name='txcode' id='txcode' value="${d['txcode'] != undefind ? d['txcode'] : '0151063'}" dynamicValue="${i['txcode']}"/>
                <input type='hidden' name='listData' id='listData' value="${d['listData'] != undefind ? d['listData'] : ''}"/>
            </div>
        </form>
        <%@ include file="/comm/jsp/bodyFooter.jsp"%>
