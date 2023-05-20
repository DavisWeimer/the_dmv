pry(main)> require './lib/facility'
#=> true

pry(main)> require './lib/vehicle'
#=> true

pry(main)> facility_1 = Facility.new({name: 'Albany DMV Office', address: '2242 Santiam Hwy SE Albany OR 97321', phone: '541-967-2014' })
#=> #<Facility:0x00000001258a3d80 @address="2242 Santiam Hwy SE Albany OR 97321", @collected_fees=0, @name="Albany DMV Office", @phone="541-967-2014", @registered_vehicles=[], @services=[]>

pry(main)> facility_2 = Facility.new({name: 'Ashland DMV Office', address: '600 Tolman Creek Rd Ashland OR 97520', phone: '541-776-6092' })
#=> #<Facility:0x000000012581e3d8 @address="600 Tolman Creek Rd Ashland OR 97520", @collected_fees=0, @name="Ashland DMV Office", @phone="541-776-6092", @registered_vehicles=[], @services=[]>

pry(main)> cruz = Vehicle.new({vin: '123456789abcdefgh', year: 2012, make: 'Chevrolet', model: 'Cruz', engine: :ice} )
#=> #<Vehicle:0x0000000135a48b08 @engine=:ice, @make="Chevrolet", @model="Cruz", @plate_type=nil, @registration_date=nil, @vin="123456789abcdefgh", @year=2012>

pry(main)> bolt = Vehicle.new({vin: '987654321abcdefgh', year: 2019, make: 'Chevrolet', model: 'Bolt', engine: :ev} )
#=> #<Vehicle:0x0000000125832180 @engine=:ev, @make="Chevrolet", @model="Bolt", @plate_type=nil, @registration_date=nil, @vin="987654321abcdefgh", @year=2019>

pry(main)> camaro = Vehicle.new({vin: '1a2b3c4d5e6f', year: 1969, make: 'Chevrolet', model: 'Camaro', engine: :ice} )
#=> #<Vehicle:0x0000000135adb610 @engine=:ice, @make="Chevrolet", @model="Camaro", @plate_type=nil, @registration_date=nil, @vin="1a2b3c4d5e6f", @year=1969>

pry(main)> facility_1.add_service('Vehicle Registration')
#=> ["Vehicle Registration"]

pry(main)> cruz.registration_date
#=> nil

pry(main)> facility_1.registered_vehicles
#=> []

pry(main)> facility_1.collected_fees
#=> 0

pry(main)> facility_1.register_vehicle(cruz)
#=> [#<Vehicle:0x0000000135a48b08...>]

pry(main)> cruz.registration_date
#=> #<Date: 2023-01-12 ((2459957j,0s,0n),+0s,2299161j)>

pry(main)> cruz.plate_type
#=> :regular

pry(main)> facility_1.registered_vehicles
#=> [#<Vehicle:0x0000000135a48b08...>]

pry(main)> facility_1.collected_fees
#=> 100

pry(main)> facility_1.register_vehicle(camaro)
#=> [#<Vehicle:0x0000000135a48b08...>, #<Vehicle:0x0000000135adb610...>]

pry(main)> camaro.registration_date
#=> #<Date: 2023-01-12 ((2459957j,0s,0n),+0s,2299161j)>

pry(main)> camaro.plate_type
#=> :antique

pry(main)> facility_1.register_vehicle(bolt)
#=> [#<Vehicle:0x0000000135a48b08...>, #<Vehicle:0x0000000135adb610...>, #<Vehicle:0x0000000125832180...>]

pry(main)> bolt.registration_date
#=> #<Date: 2023-01-12 ((2459957j,0s,0n),+0s,2299161j)>

pry(main)> bolt.plate_type
#=> :ev

pry(main)> facility_1.registered_vehicles
#=> [#<Vehicle:0x0000000135a48b08...>, #<Vehicle:0x0000000135adb610...>, #<Vehicle:0x0000000125832180...>]

pry(main)> facility_1.collected_fees
#=> 325

pry(main)> facility_2.registered_vehicles
#=> []

pry(main)> facility_2.services
#=> []

pry(main)> facility_2.register_vehicle(bolt)
#=> nil

pry(main)> facility_2.registered_vehicles
#=> []

pry(main)> facility_2.collected_fees
#=> 0