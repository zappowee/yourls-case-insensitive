This plugin requires a YOURLS build from April 2013 or newer.

If you have an older version of YOURLS, a modification to includes/functions.php is needed.

Edit includes/functions.php and find (around line 385):

function yourls_keyword_is_taken( $keyword ) {

After, add:

	// Allow plugins to short-circuit the whole function
	$pre = yourls_apply_filter( 'shunt_keyword_is_taken', false, $keyword );
	if ( false !== $pre )
		return $pre;
		
