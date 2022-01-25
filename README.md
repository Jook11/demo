# для запуска, разместить код на любой странице с конкретными настройками

<?
require($_SERVER["DOCUMENT_ROOT"]."/bitrix/header.php");
$APPLICATION->SetTitle("Title");
?>
<?
$rsGroups = CGroup::GetList ($by = "c_sort", $order = "asc", Array ("NAME" => "Рецензенты"));
$idgrup=$rsGroups->Fetch();
//echo "<pre>"; print_r($idgrup); echo "</pre>";
if(in_array($idgrup['ID'], $USER->GetUserGroupArray())):
?><a href="?logout=yes">Выйти как пользователь "Рецензент"</a><br><?
endif;?>



<?$APPLICATION->IncludeComponent(
	"my:iblock.element.add2", 
	".default", 
	array(
		"AJAX_MODE" => "N",
		"AJAX_OPTION_ADDITIONAL" => "",
		"AJAX_OPTION_HISTORY" => "N",
		"AJAX_OPTION_JUMP" => "N",
		"AJAX_OPTION_STYLE" => "Y",
		"ALLOW_DELETE" => "Y",
		"ALLOW_EDIT" => "Y",
		"CUSTOM_TITLE_DATE_ACTIVE_FROM" => "",
		"CUSTOM_TITLE_DATE_ACTIVE_TO" => "",
		"CUSTOM_TITLE_DETAIL_PICTURE" => "",
		"CUSTOM_TITLE_DETAIL_TEXT" => "",
		"CUSTOM_TITLE_IBLOCK_SECTION" => "",
		"CUSTOM_TITLE_NAME" => "Название книги",
		"CUSTOM_TITLE_PREVIEW_PICTURE" => "",
		"CUSTOM_TITLE_PREVIEW_TEXT" => "",
		"CUSTOM_TITLE_TAGS" => "",
		"DEFAULT_INPUT_SIZE" => "30",
		"DETAIL_TEXT_USE_HTML_EDITOR" => "N",
		"ELEMENT_ASSOC" => "CREATED_BY",
		"GROUPS" => array(
			0 => $idgrup['ID'],
		),
		"IBLOCK_ID" => "47",
		"IBLOCK_TYPE" => "content",
		"LEVEL_LAST" => "Y",
		"MAX_FILE_SIZE" => "0",
		"MAX_LEVELS" => "100000",
		"MAX_USER_ENTRIES" => "100000",
		"NAV_ON_PAGE" => "10",
		"PREVIEW_TEXT_USE_HTML_EDITOR" => "N",
		"PROPERTY_CODES" => array(
			1 => "100",
			2 => "101",
			3 => "102",
			4 => "103",
			5 => "104",
			6 => "NAME",
		),
		"PROPERTY_CODES_REQUIRED" => array(
			0 => "101",
			1 => "102",
			2 => "103",
			3 => "104",
			4 => "NAME",
		),
		"RESIZE_IMAGES" => "N",
		"SEF_MODE" => "N",
		"STATUS" => "ANY",
		"STATUS_NEW" => "N",
		"USER_MESSAGE_ADD" => "",
		"USER_MESSAGE_EDIT" => "",
		"USE_CAPTCHA" => "N",
		"COMPONENT_TEMPLATE" => ".default"
	),
	false
);?><?require($_SERVER["DOCUMENT_ROOT"]."/bitrix/footer.php");?>
