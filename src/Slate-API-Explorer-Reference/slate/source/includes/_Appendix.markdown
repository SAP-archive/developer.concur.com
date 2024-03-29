
## Appendix


### Search 

![./media/image1.png](./images/search.png)

#### Request
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">
  <Header xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <authentication xmlns="http://www.concur.com/webservice/auth">
      <userid>testLogin123</userid>
      <password>txxxxxxxxxxxx;</password>
    </authentication>
  </Header>
  <Body xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <OTA_HotelSearchRQ xmlns="http://www.opentravel.org/OTA/2003/05"
                       EchoToken="5ADE581A-8A7C-4DA5-A67B-EED4E58A80E2"
                       Version="4" PrimaryLangID="en" AltLangID="en" MaxResponses="100">
      <POS>
        <Source ISOCurrency="USD"></Source>
      </POS>
      <Criteria>
        <Criterion>
          <Position Latitude="52.559720" Longitude="13.287780"></Position>
          <RefPoint></RefPoint>
          <Radius Distance="5" DistanceMax="30" UnitOfMeasureCode="1"></Radius>
          <StayDateRange Start="2018-02-12" End="2018-02-13"></StayDateRange>
        </Criterion>
      </Criteria>
    </OTA_HotelSearchRQ>
  </Body>
</Envelope>
 ```

#### Response
```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"/>
  <soap:Body>
    <OTA_HotelSearchRS xmlns="http://www.opentravel.org/OTA/2003/05" xmlns:ns2="http://www.concur.com/webservice/auth" AltLangID="fr" EchoToken="FC6F5CDE-2D55-49A4-AE22-056AF980ADF4" PrimaryLangID="fr" Version="4">
      <Success/>
      <Properties>
        <Property ChainName="Appart City" HotelCode="399671" HotelName="Appart'City Aix en Provence - La Duranne Residence de Tourisme">
          <Position Latitude="43.49205" Longitude="5.351965"/>
          <Address>
            <AddressLine>300 avenue du Grand Vallat</AddressLine>
            <CityName>Les Milles</CityName>
            <PostalCode>13290</PostalCode>
            <CountryName Code="FR">French Republic France</CountryName>
          </Address>
          <Award Rating="2"/>
          <HotelAmenity Code="68"/>
          <HotelAmenity Code="198"/>
          <HotelAmenity Code="71"/>
          <HotelAmenity Code="101"/>
          <HotelAmenity Code="33"/>
          <Policy CheckInTime="14:00:00" CheckOutTime="12:00:00"/>
          <TPA_Extensions>
            <HotelPreference>not_preferred</HotelPreference>
            <TPA_HotelPreviewImageURI>
              <URL>https://foto.hrsstatic.com/fotos/1/3/75/75/80/FFFFFF/http%3A%2F%2Ffoto-origin.hrsstatic.com%2Ffoto%2F3%2F9%2F9%2F6%2Fteaser_399671.jpg/v1M9Y02mJkgafy7d97qkhw%3D%3D/128%2C85/6/AppartCity_Aix_en_Provence_La_Duranne_Residence_de_Tourisme-Les_Milles_Aix-en-Provence-Exterior_view-3-399671.jpg</URL>
            </TPA_HotelPreviewImageURI>
          </TPA_Extensions>
        </Property>
        <Property>
          ... and another properties follow here for all the returned hotels
        </Property>
      </Properties>
    </OTA_HotelSearchRS>
  </soap:Body>
</soap:Envelope>
```

#### Availability

The initial Search request (see above) is followed up by an multi-property Availability request.  In the example request below Concur requests the availability for 13 properties.  This could because the initial search only yielded 13 properties or the configuration per vendor is set to request availability for a maximum of 13 properties.

#### Request

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">
  <Header xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <authentication xmlns="http://www.concur.com/webservice/auth">
      <userid>testLogin123</userid>
      <password>txxxxxxxxxxxx;</password>
    </authentication>
  </Header>
  <Body xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <OTA_HotelAvailRQ xmlns="http://www.opentravel.org/OTA/2003/05"
                      EchoToken="5ADE581A-8A7C-4DA5-A67B-EED4E58A80E2"
                      Version="5" PrimaryLangID="en" AltLangID="en">
      <POS>
        <Source ISOCurrency="USD"></Source>
      </POS>
      <AvailRequestSegments>
        <AvailRequestSegment>
          <HotelSearchCriteria>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="50709"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="468159"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="584875"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="765336"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="70346"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="52198"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="697768"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="14411"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="436533"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="459980"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="419430"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="92103"></HotelRef>
            </Criterion>
            <Criterion>
              <HotelRef ChainCode="ZZ" HotelCode="252272"></HotelRef>
            </Criterion>
          </HotelSearchCriteria>
          <StayDateRange Start="2018-02-12" End="2018-02-13"></StayDateRange>
          <RoomStayCandidates>
            <RoomStayCandidate>
              <GuestCounts>
                <GuestCount AgeQualifyingCode="10" Count="1"></GuestCount>
              </GuestCounts>
            </RoomStayCandidate>
          </RoomStayCandidates>
        </AvailRequestSegment>
      </AvailRequestSegments>
    </OTA_HotelAvailRQ>
  </Body>
</Envelope>
```

#### Response

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"/>
  <soap:Body>
    <OTA_HotelAvailRS xmlns="http://www.opentravel.org/OTA/2003/05" xmlns:ns2="http://www.concur.com/webservice/auth" AltLangID="fr" EchoToken="FC6F5CDE-2D55-49A4-AE22-056AF980ADF4" PrimaryLangID="fr" Version="5">
      <Success/>
      <RoomStays>
        <RoomStay>
          <RoomTypes>
            <RoomType RoomID="b3da298f">
              <RoomDescription>
                <Text>La chambre standard est équipée de douche/WC ou de baignoire/WC.</Text>
              </RoomDescription>
              <Amenities>
                <Amenity ExistsCode="1" RoomAmenity="55"/>
                <Amenity ExistsCode="1" RoomAmenity="56"/>
                <Amenity ExistsCode="1" RoomAmenity="4"/>
                <Amenity ExistsCode="1" RoomAmenity="28"/>
                <Amenity ExistsCode="1" RoomAmenity="210"/>
                <Amenity ExistsCode="1" RoomAmenity="92"/>
                <Amenity ExistsCode="1" RoomAmenity="2"/>
                <Amenity ExistsCode="1" RoomAmenity="126"/>
                <Amenity ExistsCode="1" RoomAmenity="19"/>
                <Amenity ExistsCode="1" RoomAmenity="13"/>
                <Amenity ExistsCode="1" RoomAmenity="96"/>
                <Amenity ExistsCode="1" RoomAmenity="50"/>
                <Amenity ExistsCode="1" RoomAmenity="69"/>
                <Amenity ExistsCode="1" RoomAmenity="107"/>
                <Amenity ExistsCode="1" RoomAmenity="10"/>
              </Amenities>
            </RoomType>
          </RoomTypes>
          <RatePlans>
            <RatePlan AvailabilityStatus="AvailableForSale" PrepaidIndicator="false" RatePlanID="TOGG3BU">
              <Guarantee GuaranteeType="GuaranteeRequired">
                <Deadline AbsoluteDeadline="2019-05-08T23:59:59"/>
              </Guarantee>
              <CancelPenalties>
                <CancelPenalty NonRefundable="false">
                  <Deadline AbsoluteDeadline="2019-05-08T23:59:59" OffsetDropTime="BeforeArrival" OffsetTimeUnit="Day"
                            OffsetUnitMultiplier="14"/>
                </CancelPenalty>
              </CancelPenalties>
              <MealsIncluded Breakfast="false" Dinner="false" Lunch="false"/>
            </RatePlan>
          </RatePlans>
          <RoomRates>
            <RoomRate RatePlanID="TOGG3BU" RoomID="b3da298f">
              <Rates>
                <Rate ChargeType="18" GuaranteedInd="true" NumberOfUnits="1" RateTimeUnit="FullDuration"
                      RoomPricingType="Per stay" UnitMultiplier="1">
                  <PaymentPolicies>
                    <GuaranteePayment>
                      <AcceptedPayments>
                        <AcceptedPayment>
                          <PaymentCard>
                            <CardType>VISA</CardType>
                          </PaymentCard>
                        </AcceptedPayment>
                      </AcceptedPayments>
                    </GuaranteePayment>
                    <GuaranteePayment>
                      <AcceptedPayments>
                        <AcceptedPayment>
                          <PaymentCard>
                            <CardType>Mastercard</CardType>
                          </PaymentCard>
                        </AcceptedPayment>
                      </AcceptedPayments>
                    </GuaranteePayment>
                  </PaymentPolicies>
                  <Total AmountAfterTax="161.10" AmountBeforeTax="152.70" CurrencyCode="EUR" DecimalPlaces="2"/>
                  <RateDescription>
                    <Text>Tarif promotionnel</Text>
                    <Text>Gratuit pour les clients HRS: Quotidien gratuit, Parking attenant à l'hôtel</Text>
                  </RateDescription>
                </Rate>
              </Rates>
            </RoomRate>
          </RoomRates>
          <GuestCounts>
            <GuestCount Count="1"/>
          </GuestCounts>
          <TimeSpan End="2019-05-23" Start="2019-05-22"/>
          <BasicPropertyInfo HotelCode="36151" HotelName="Château de la Pioline">
            <Address>
              <AddressLine>260 Rue Guillaume du Vair</AddressLine>
              <CityName>AIX EN PROVENCE</CityName>
              <PostalCode>13546</PostalCode>
              <CountryName Code="FR">French Republic France</CountryName>
            </Address>
            <ContactNumbers>
              <ContactNumber PhoneNumber="33442522727"/>
            </ContactNumbers>
          </BasicPropertyInfo>
        </RoomStay>
        <RoomStay>
          <RoomTypes>
            <RoomType RoomID="f7631619">
              <RoomDescription>
                <Text>La chambre standard est équipée de douche/WC ou de baignoire/WC.</Text>
              </RoomDescription>
              <Amenities>
                <Amenity ExistsCode="1" RoomAmenity="55"/>
                <Amenity ExistsCode="1" RoomAmenity="56"/>
                <Amenity ExistsCode="1" RoomAmenity="4"/>
                <Amenity ExistsCode="1" RoomAmenity="28"/>
                <Amenity ExistsCode="1" RoomAmenity="210"/>
                <Amenity ExistsCode="1" RoomAmenity="92"/>
                <Amenity ExistsCode="1" RoomAmenity="2"/>
                <Amenity ExistsCode="1" RoomAmenity="126"/>
                <Amenity ExistsCode="1" RoomAmenity="19"/>
                <Amenity ExistsCode="1" RoomAmenity="13"/>
                <Amenity ExistsCode="1" RoomAmenity="96"/>
                <Amenity ExistsCode="1" RoomAmenity="50"/>
                <Amenity ExistsCode="1" RoomAmenity="69"/>
                <Amenity ExistsCode="1" RoomAmenity="107"/>
                <Amenity ExistsCode="1" RoomAmenity="10"/>
              </Amenities>
            </RoomType>
          </RoomTypes>
          <RatePlans>
            <RatePlan AvailabilityStatus="AvailableForSale" PrepaidIndicator="false" RatePlanID="MB4YV34">
              <Guarantee GuaranteeType="Deposit"/>
              <CancelPenalties>
                <CancelPenalty NonRefundable="true">
                  <Deadline AbsoluteDeadline="2019-04-15T12:51:47"/>
                </CancelPenalty>
              </CancelPenalties>
              <MealsIncluded Breakfast="false" Dinner="false" Lunch="false"/>
            </RatePlan>
          </RatePlans>
          <RoomRates>
            <RoomRate RatePlanID="MB4YV34" RoomID="f7631619">
              <Rates>
                <Rate ChargeType="18" GuaranteedInd="true" NumberOfUnits="1" RateTimeUnit="FullDuration"
                      RoomPricingType="Per stay" UnitMultiplier="1">
                  <PaymentPolicies>
                    <GuaranteePayment>
                      <AcceptedPayments>
                        <AcceptedPayment>
                          <PaymentCard>
                            <CardType>VISA</CardType>
                          </PaymentCard>
                        </AcceptedPayment>
                      </AcceptedPayments>
                    </GuaranteePayment>
                    <GuaranteePayment>
                      <AcceptedPayments>
                        <AcceptedPayment>
                          <PaymentCard>
                            <CardType>Mastercard</CardType>
                          </PaymentCard>
                        </AcceptedPayment>
                      </AcceptedPayments>
                    </GuaranteePayment>
                  </PaymentPolicies>
                  <Total AmountAfterTax="149.00" AmountBeforeTax="141.23" CurrencyCode="EUR" DecimalPlaces="2"/>
                  <RateDescription>
                    <Text>Hot Deal</Text>
                    <Text>Gratuit pour les clients HRS: Quotidien gratuit, Parking attenant à l'hôtel</Text>
                  </RateDescription>
                </Rate>
              </Rates>
            </RoomRate>
          </RoomRates>
          <GuestCounts>
            <GuestCount Count="1"/>
          </GuestCounts>
          <TimeSpan End="2019-05-23" Start="2019-05-22"/>
          <BasicPropertyInfo HotelCode="36151" HotelName="Château de la Pioline">
            <Address>
              <AddressLine>260 Rue Guillaume du Vair</AddressLine>
              <CityName>AIX EN PROVENCE</CityName>
              <PostalCode>13546</PostalCode>
              <CountryName Code="FR">French Republic France</CountryName>
            </Address>
            <ContactNumbers>
              <ContactNumber PhoneNumber="33442522727"/>
            </ContactNumbers>
          </BasicPropertyInfo>
        </RoomStay>
        <RoomStay>
          ... and another RoomStay nodes follow here for all the returned rooms for all the hotels (properties) per
          Availability request
        </RoomStay>
      </RoomStays>
    </OTA_HotelAvailRS>
  </soap:Body>
</soap:Envelope>
```


#### Search results displayed

Search results page displaying hotels, based on Search response, and their rates, based on Availability response:

![./media/image1.png](./images/search_results.png)


WIth Availability response also cancellation information comes which can be displayed in separate popup:

![./media/image1.png](./images/17.png)



#### Hotel Description

![./media/image1.png](./images/5_link.png)

#### Request
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">
  <Header xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <authentication xmlns="http://www.concur.com/webservice/auth">
      <userid>testLogin123</userid>
      <password>txxxxxxxxxxxx;</password>
    </authentication>
  </Header>
  <Body xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <OTA_HotelDescriptiveInfoRQ xmlns="http://www.opentravel.org/OTA/2003/05"
                                EchoToken="A78F3641-8674-43F9-B58C-AD928D1A75D9"
                                Version="3" PrimaryLangID="en" AltLangID="en">
      <POS>
        <Source ISOCurrency="USD"></Source>
      </POS>
      <HotelDescriptiveInfos>
        <HotelDescriptiveInfo ChainCode="ZZ" HotelCode="419430"></HotelDescriptiveInfo>
      </HotelDescriptiveInfos>
    </OTA_HotelDescriptiveInfoRQ>
  </Body>
</Envelope>
```

#### Response
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"/>
  <soap:Body>
    <OTA_HotelDescriptiveInfoRS xmlns="http://www.opentravel.org/OTA/2003/05"
                                xmlns:ns2="http://www.concur.com/webservice/auth">
      <Success/>
      <HotelDescriptiveContents>
        <HotelDescriptiveContent ChainCode="ZZ" HotelCode="419430" HotelName="Courtyard Prague Airport">
          <HotelInfo>
            <Descriptions>
              <DescriptiveText>Prague (PRG): The Europort building which housed the hotel is located in front of the
                arrivial and departure halls at Prague-ruzyne Airport. The hotel will have direct access to the
                airport’s infrastructure and offer connections to both the walkway and transporation routes. The
                conveniently located Courtyard Prague Airport provides its guests upscale accommodation outside the
                buzzing city centre. Kept in a cosy elegant design, the comfortable rooms are fitted with coffee and tea
                maker and nice sitting and working area. The magnificent atrium with its modern structure and nice
                garden invites to stay and relax. Directly situated at Prague’s international airport, the hotel is
                about 16 kilometres from the city centre and the historic castle. In the nearby surroundings, guests can
                enjoy horseback riding, biking or kayaking. Oléo Pazzo Mediterranean Bistro is a contemporary restaurant
                decorated in warm and coulourful style with a show kitchen and a trendy bar. Other features are a
                fitness,a business center,meeting rooms.
              </DescriptiveText>
            </Descriptions>
          </HotelInfo>
          <MultimediaDescriptions>
            <MultimediaDescription>
              <ImageItems>
                <ImageItem>
                  <ImageFormat>
                    <URL>http://iut-foto-origin.hrsstatic.com/foto/3/8/9/8/389886/389886_fi_451616.jpg</URL>
                  </ImageFormat>
                </ImageItem>
                <ImageItem>
                  <ImageFormat>
                    <URL>http://iut-foto-origin.hrsstatic.com/foto/3/8/9/8/389886/389886_u_6302064.jpg</URL>
                  </ImageFormat>
                </ImageItem>
                <ImageItem>
                  <ImageFormat>
                    <URL>http://iut-foto-origin.hrsstatic.com/foto/3/8/9/8/389886/389886_u_451896.jpg</URL>
                  </ImageFormat>
                </ImageItem>
              </ImageItems>
            </MultimediaDescription>
          </MultimediaDescriptions>
          <TPA_Extensions>
            <Description Name="First Description">
              <Text>First line of first description.</Text>
              <Text>Second line of first description.</Text>
            </Description>
            <Description>
              <Text>Second description without name.</Text>
            </Description>
          </TPA_Extensions>
        </HotelDescriptiveContent>
      </HotelDescriptiveContents>
    </OTA_HotelDescriptiveInfoRS>
  </soap:Body>
</soap:Envelope>
```


#### Hotel Details displayed

![./media/image1.png](./images/5_1.png)


#### Reservation

![./media/image1.png](./images/4.png)
![./media/image1.png](./images/6.png)

![./media/image1.png](./images/6_1.png)
![./media/image1.png](./images/6_2.png)

#### Request
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">
  <Header xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <authentication xmlns="http://www.concur.com/webservice/auth">
      <userid>testLogin123</userid>
      <password>txxxxxxxxxxxx;</password>
    </authentication>
  </Header>
  <Body xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <OTA_HotelResRQ xmlns="http://www.opentravel.org/OTA/2003/05"
                    EchoToken="6C85DDBD-EB62-444D-B2C3-F59BDF65BE98"
                    Version="6" PrimaryLangID="en" AltLangID="en">
      <POS>
        <Source ISOCurrency="USD"></Source>
      </POS>
      <HotelReservations>
        <HotelReservation>
          <RoomStays>
            <RoomStay>
              <RatePlans>
                <RatePlan RatePlanID="XNFYP4I">
                  <Guarantee GuaranteeType="CC/DC/Voucher">
                    <GuaranteesAccepted>
                      <GuaranteeAccepted>
                        <PaymentCard CardCode="VI" ExpireDate="1220">
                          <CardType Code="VI">VISA</CardType>
                          <CardHolderName>HOTELSERVICEAMADEUS TESTUSERMOCK</CardHolderName>
                        </PaymentCard>
                      </GuaranteeAccepted>
                    </GuaranteesAccepted>
                  </Guarantee>
                </RatePlan>
              </RatePlans>
              <TimeSpan Start="2018-02-12" End="2018-02-13"></TimeSpan>
              <BasicPropertyInfo HotelCode="419430"></BasicPropertyInfo>
            </RoomStay>
          </RoomStays>
          <ResGuests>
            <ResGuest>
              <Profiles>
                <ProfileInfo>
                  <Profile>
                    <Customer Gender="Unknown">
                      <PersonName Language="en">
                        <GivenName>HOTELSERVICEAMADEUS</GivenName>
                        <Surname>TESTUSERMOCK</Surname>
                      </PersonName>
                      <Telephone PhoneNumber="3141011001"></Telephone>
                      <Email>hrs_hs2_amadeus_mock@concurautm3.com</Email>
                      <Address>
                        <AddressLine>123 Sesame St.</AddressLine>
                        <CityName>Alexandria</CityName>
                        <PostalCode>22314</PostalCode>
                        <StateProv></StateProv>
                        <CountryName Code="US">USA</CountryName>
                      </Address>
                      <CitizenCountryName Code="US"></CitizenCountryName>
                    </Customer>
                    <CompanyInfo>
                      <CompanyName>CONCURTECH</CompanyName>
                    </CompanyInfo>
                  </Profile>
                </ProfileInfo>
              </Profiles>
              <GuestCounts>
                <GuestCount Count="1"></GuestCount>
              </GuestCounts>
            </ResGuest>
          </ResGuests>
        </HotelReservation>
      </HotelReservations>
    </OTA_HotelResRQ>
  </Body>
</Envelope>
```


#### Response
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"/>
  <soap:Body>
    <OTA_HotelResRS xmlns="http://www.opentravel.org/OTA/2003/05"
                    xmlns:ns2="http://www.concur.com/webservice/auth"
                    ResResponseType="Reserved">
      <Success/>
      <HotelReservations>
        <HotelReservation>
          <UniqueID ID="88618333"/>
          <RoomStays>
            <RoomStay>
              <RatePlans>
                <RatePlan RatePlanID="EZ57LL7">
                  <CancelPenalties CancelPolicyIndicator="true">
                    <CancelPenalty>
                      <PenaltyDescription>
                        <Text>test cancel policy 1</Text>
                      </PenaltyDescription>
                    </CancelPenalty>
                    <CancelPenalty>
                      <Deadline AbsoluteDeadline="2018-02-22T18:00"/>
                    </CancelPenalty>
                  </CancelPenalties>
                </RatePlan>
              </RatePlans>
              <RoomRates>
                <RoomRate>
                  <Rates>
                    <Rate RoomPricingType="Per stay">
                      <PaymentPolicies>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="VI"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="MC"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="CA"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="IK"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="AX"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                      </PaymentPolicies>
                      <Total AmountAfterTax="85.00" AmountBeforeTax="85.00" CurrencyCode="EUR"/>
                    </Rate>
                  </Rates>
                </RoomRate>
              </RoomRates>
              <TimeSpan End="2018-02-23" Start="2018-02-22"/>
              <BasicPropertyInfo HotelCode="50709" HotelName="Alexander Plaza">
                <Address>
                  <AddressLine>Rosenstr. 1</AddressLine>
                  <CityName>Berlin</CityName>
                  <CountryName Code="DEU">Federal Republic of Germany</CountryName>
                  <StateProv StateCode="BE">Berlin disctrict</StateProv>
                  <PostalCode>BE123</PostalCode>
                </Address>
                <ContactNumbers>
                  <ContactNumber PhoneNumber="3024001722"/>
                </ContactNumbers>
              </BasicPropertyInfo>
            </RoomStay>
          </RoomStays>
          <ResGuests>
            <ResGuest>
              <Profiles>
                <ProfileInfo>
                  <Profile>
                    <Customer>
                      <PersonName>
                        <GivenName>TESTER</GivenName>
                        <Surname>Testovic</Surname>
                      </PersonName>
                    </Customer>
                  </Profile>
                </ProfileInfo>
              </Profiles>
            </ResGuest>
          </ResGuests>
          <ResGlobalInfo>
            <Comments>
              <Comment Name="Comment 1">
                <Text>First line of Comment 1.</Text>
                <Text>Second line of Comment 1.</Text>
              </Comment>
              <Comment>
                <Text>First line of Comment 2 without name.</Text>
              </Comment>
            </Comments>
          </ResGlobalInfo>
        </HotelReservation>
      </HotelReservations>
    </OTA_HotelResRS>
  </soap:Body>
</soap:Envelope>
```


#### Read

![./media/image1.png](./images/7.png)
![./media/image1.png](./images/8.png)
![./media/image1.png](./images/9.png)

#### Request
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">
  <Header xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <authentication xmlns="http://www.concur.com/webservice/auth">
      <userid>testLogin123</userid>
      <password>txxxxxxxxxxxx;</password>
    </authentication>
  </Header>
  <Body xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <OTA_ReadRQ xmlns="http://www.opentravel.org/OTA/2003/05"
                EchoToken="4E1B8BF4-ACBD-4709-9FCC-B59EB2550086"
                Version="5.002" PrimaryLangID="en" AltLangID="en">
      <POS>
        <Source ISOCurrency="USD"></Source>
      </POS>
      <UniqueID Type="14" ID="88618333"></UniqueID>
    </OTA_ReadRQ>
  </Body>
</Envelope>
```


#### Response
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"/>
  <soap:Body>
    <OTA_HotelResRS xmlns="http://www.opentravel.org/OTA/2003/05"
                    xmlns:ns2="http://www.concur.com/webservice/auth"
                    ResResponseType="Reserved">
      <Success/>
      <HotelReservations>
        <HotelReservation>
          <UniqueID ID="88621190"/>
          <RoomStays>
            <RoomStay>
              <RatePlans>
                <RatePlan RatePlanID="P4PGI5Q">
                  <CancelPenalties CancelPolicyIndicator="true">
                    <CancelPenalty>
                      <PenaltyDescription>
                        <Text>test cancel policy 1</Text>
                      </PenaltyDescription>
                    </CancelPenalty>
                    <CancelPenalty>
                      <PenaltyDescription>
                        <Text>test cancel policy 2</Text>
                      </PenaltyDescription>
                      <PenaltyDescription>
                        <Text>test cancel policy 3</Text>
                      </PenaltyDescription>
                    </CancelPenalty>
                    <CancelPenalty>
                      <Deadline AbsoluteDeadline="2018-02-22T18:00"/>
                    </CancelPenalty>
                  </CancelPenalties>
                </RatePlan>
              </RatePlans>
              <RoomRates>
                <RoomRate>
                  <Rates>
                    <Rate RoomPricingType="Per stay">
                      <PaymentPolicies>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="VI"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="MC"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="CA"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="IK"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                        <GuaranteePayment>
                          <AcceptedPayments>
                            <AcceptedPayment>
                              <PaymentCard CardCode="AX"/>
                            </AcceptedPayment>
                          </AcceptedPayments>
                        </GuaranteePayment>
                      </PaymentPolicies>
                      <Total AmountAfterTax="208.95" AmountBeforeTax="208.95" CurrencyCode="EUR"/>
                    </Rate>
                  </Rates>
                </RoomRate>
              </RoomRates>
              <TimeSpan End="2018-02-23" Start="2018-02-22"/>
              <BasicPropertyInfo ChainCode="1609" HotelCode="10517" HotelName="Radisson Blu Hotel">
                <Address>
                  <AddressLine>Karl-Liebknecht-Str. 3</AddressLine>
                  <CityName>Berlin</CityName>
                  <CountryName Code="DEU">Federal Republic of Germany</CountryName>
                  <StateProv StateCode="BE">Berlin disctrict</StateProv>
                  <PostalCode>BE123</PostalCode>
                </Address>
                <ContactNumbers>
                  <ContactNumber PhoneNumber="30238280"/>
                </ContactNumbers>
              </BasicPropertyInfo>
            </RoomStay>
          </RoomStays>
          <ResGuests>
            <ResGuest>
              <Profiles>
                <ProfileInfo>
                  <Profile>
                    <Customer>
                      <PersonName>
                        <GivenName>TESTER</GivenName>
                        <Surname>Testovic</Surname>
                      </PersonName>
                    </Customer>
                  </Profile>
                </ProfileInfo>
              </Profiles>
            </ResGuest>
          </ResGuests>
          <ResGlobalInfo>
            <Comments>
              <Comment Name="Comment 1">
                <Text>First line of Comment 1.</Text>
                <Text>Second line of Comment 1.</Text>
              </Comment>
              <Comment>
                <Text>First line of Comment 2 without name.</Text>
              </Comment>
            </Comments>
          </ResGlobalInfo>
        </HotelReservation>
      </HotelReservations>
    </OTA_HotelResRS>
  </soap:Body>
</soap:Envelope>
```
#### Itinerary displayed

![./media/image1.png](./images/10_1.png)
![./media/image1.png](./images/10_2.png)

#### Cancel

![./media/image1.png](./images/12.png)
![./media/image1.png](./images/14.png)

#### Request

```xml
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">
  <Header xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <authentication xmlns="http://www.concur.com/webservice/auth">
      <userid>testLogin123</userid>
      <password>txxxxxxxxxxxx;</password>
    </authentication>
  </Header>
  <Body xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <OTA_CancelRQ xmlns="http://www.opentravel.org/OTA/2003/05" CancelType="Cancel"
                  EchoToken="2186EB84-23D9-4977-B8A5-B5083C8DE228"
                  Version="3" PrimaryLangID="en" AltLangID="en">
      <POS>
        <Source ISOCurrency="USD"></Source>
      </POS>
      <UniqueID Type="14" ID="88618333"></UniqueID>
    </OTA_CancelRQ>
  </Body>
</Envelope>
```


#### Response
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"/>
  <soap:Body>
    <OTA_CancelRS xmlns="http://www.opentravel.org/OTA/2003/05"
                  xmlns:ns2="http://www.concur.com/webservice/auth"
                  Status="Cancelled">
      <Success/>
      <UniqueID ID="88618333" Type="14"/>
      <UniqueID ID="27607" Type="15"/>
    </OTA_CancelRS>
  </soap:Body>
</soap:Envelope>
```

![./media/image1.png](./images/15.png)
![./media/image1.png](./images/16.png)
