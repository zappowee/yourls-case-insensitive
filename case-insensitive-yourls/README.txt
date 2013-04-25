At the moment, this plugin requires a modification to the standard YOURLS file includes/functions.php.
Hopefully, a filter will be added to the core code of YOURLS that will eliminate the need for this file modification in the future.

Edit includes/functions.php and find (around line 385):

function yourls_keyword_is_taken( $keyword ) {

After, add:

	// Allow plugins to short-circuit the whole function
	$pre = yourls_apply_filter( 'shunt_keyword_is_taken', false, $keyword );
	if ( false !== $pre )
		return $pre;
		
