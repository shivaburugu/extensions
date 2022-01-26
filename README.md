# extensions
 library is a set of Kotlin extensions


private var fusedLocationClient: FusedLocationProviderClient? = null

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        fusedLocationClient = LocationServices.getFusedLocationProviderClient(this)
        if (ContextCompat.checkSelfPermission( this, android.Manifest.permission.ACCESS_COARSE_LOCATION ) != PackageManager.PERMISSION_GRANTED ) {
            Toast.makeText(this, "Permission not granted before", Toast.LENGTH_LONG).show()
        } else {
            fusedLocationClient?.lastLocation?.addOnSuccessListener { location : Location? ->
                    Toast.makeText(this, "location permission granted location is ${location?.latitude} and ${location?.longitude}", Toast.LENGTH_LONG).show()
                }
        }
    }
