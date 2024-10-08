# Mpox Immunization { #mpox-epi-design }

## Introduction and Background

Version 0.0.1 of the Mpox Vaccine Delivery metadata package has been developed as an installable solution for countries to update their DHIS2-based health management information systems (HMIS) and immunization data systems, in accordance with the preliminary WHO guidance on developing national deployment and vaccination plans for Mpox.
The objectives of the Mpox aggregated package are:

To monitor the vaccination activities and their evolution within the target populations;
- Rapidly detect uptake trends, as well as potential red flags such as drop-out rates;
- Provide geographical information about the roll-out of the vaccination efforts.

The **Mpox Aggregate System Design** document outlines the design principles and global technical guidance used to create a WHO standard metadata package for monitoring Mpox vaccination delivery. This document is intended to be utilized by DHIS2 implementers at both country and regional levels, supporting the implementation and localization of the package based on local requirements and national guidelines.

This metadata package can be applied for direct electronic reporting by staff at vaccination sites or by higher-level personnel, or used as a set of “target” metadata for aggregating individual-level data from electronic, mobile, or paper-based data collection tools. The analytics and dashboards included in these packages are designed to support the routine analysis and utilization of Mpox vaccine data at both national and sub-national levels.

The **Vaccine Delivery digital data package** was developed in response to an expressed need from countries to rapidly adapt a solution for managing data originating from planned or undertaken immunization efforts. UiO (University of Oslo) has developed the Mpox toolkits for both aggregated and individual data in order to enable countries to select the model most appropriate for their context, given workload and available resources. 

These toolkits are designed to help countries better manage and utilize their Mpox vaccine delivery data, facilitating more effective national and regional vaccination campaigns.
Digital data packages are optimized for Android data collection with the DHIS2 Capture App, free to download on the [GooglePlay store](https://play.google.com/store/apps/details?id=com.dhis2&hl=en).

## Structure and Design

Building on the products, design, and lessons learned from the [COVID-19 vaccine delivery toolkit](https://docs.dhis2.org/en/implement/health/covid-19-vaccine-delivery/covac-aggregate/design.html#cvc-agg-design), this Mpox toolkit also incorporates extensive feedback loops received over the past few years from the Health Information Systems Program (HISP) network and partner countries. This approach ensures that the package is optimized to address both immediate and long-term needs for Mpox vaccination. It has been designed to provide a flexible, scalable, and rapid solution for countries integrating Mpox into their existing health systems, as well as for those that historically have not included Mpox in their reporting systems and now face the introduction of a novel antigen in the context of epidemic circumstances.

These models and their relative benefits/limitations are summarized below:

- Aggregated data model: 
  - Suitable for countries that require a more streamlined process with fewer data entry points, focusing on key indicators and trends.
  - Enables daily reporting of key aggregate data points about vaccination activities and stock management.
  - Low complexity, easy to implement. Most manageable when case numbers are high, or wherever individual data entry is not possible due to the complexity of the tracker instance or to the burden of the vaccination activities compared to the data entry ones.
 
- Individual data model: 
  - Provides more granular insights, allowing for detailed tracking of vaccination status at the individual level, but requires more intensive data management capacity.
  - Enrolls a case and tracks over time the vaccination schedules of the patients
  - Highly granular data and multiple time dimensions for analysis can support decentralized workflow, all events linked to the case.
 
### Aggregate EPI Mpox Design

The aggregate COVIDVAC package includes:

- Monthly aggregate data set and data elements for Mpox vaccination delivery
- Annual aggregate dataset for the total and/or target population groups
- Core indicators for both datasets
- Dashboard

#### EPI - Mpox Immunzation Dataset

Similar to the [C19 aggregate toolkit](https://docs.dhis2.org/en/implement/health/covid-19-vaccine-delivery/covac-aggregate/design.html#1-introduction) for vaccine distribution, the packaged dataset is organized in a flat structure, divided into three key sections based on at-risk groups and targeted vaccination efforts. The global toolkit highlights three primary groups: Health Care Workers (HCWs), Veterinarians and Animal Handlers—given the zoonotic nature of the Mpox virus—and a generic "Other" population category. This "Other" category can either represent the broader population or be customized and expanded to include additional target groups requiring more detailed monitoring. The data is mutually exclusive among the different sections, meaning that the data inserted in this section represent all the people who are not categorized as HCWs or Veterinarians/Animal handlers.
This flexible design allows countries to adapt the dataset structure to their specific needs, ensuring comprehensive tracking across all relevant risk groups.

All sections relevant to the vaccine vaccine administration are disaggregated by age groups (0-4, 5-11, 12-17, 18-59, 60+ years), and by sex (female/male). Disaggregations can be adapted locally based on necessity and protocols.

The dataset is designed to accommodate a single vaccine. However, if additional vaccines become available for mpox immunization efforts, it is recommended to follow a similar approach to the C19 module by using [attributes](https://docs.dhis2.org/en/implement/health/covid-19-vaccine-delivery/covac-aggregate/design.html#4-datasets) to differentiate between the various vaccines.

![Vaccine administration by target groups](resources/image/epimpox_001.png)

The dataset includes a simple section on AEFIs disaggregated by seriousness. 

![AEFIs](resources/image/epimpox_002.png)

Finally, a section on staff expected and available at point of care. This section is aimed at providing a snapshot of the availability of medical staff during the roll-out of the vaccination activities.

![Staff availability](resources/image/epimpox_003.png)

#### Population Dataset

The “Population Mpox Immunisation” dataset can either be assigned at district or health site level depending on the availability of updated and reliable demographic data.

The dataset has been designed to be flexible on the front of the availability of demographic data - each section has different levels of disaggregation. Countries are therefore not expected to fill in all the sections. In turn, this means that upon the package’s implementation, the unnecessary sections could be removed according to the data available locally. 
Depending on the chosen section, the analysis of the data will have to consider the different denominators to monitor coverage.

The global population section takes into account age and sex disaggregations. Depending on the availability of demographic data, the disaggregation could be maintained or removed to just report a non-disaggregated value. The disaggregation is the same as the one proposed in teh vaccination administration section of the EPI-Mpox Immunisation dataset. 

![Population by age and sex](resources/image/epimpox_004.png)

The values encoded in this population section are used in the indicators for the global (all) coverage. 
To accurately monitor target populations as distinct groups, it is crucial to have denominators available to calculate vaccination coverage within those groups. These denominators can be found in the second tab of the population dataset. While the variables in this tab are not disaggregated, local implementers are responsible for determining which population data best suits their needs and assessing the feasibility of obtaining further disaggregation If implementers choose to rely on targeted population denominators that include age and sex disaggregation, the data in the first tab of the population dataset should be removed and disregarded. In such cases, the global population indicators will need to be adjusted accordingly to reflect the disaggregated data.

![Target population](resources/image/epimpox_005.png)

### Mpox Electronic Immunisation Registry (EIR)

The design of the Mpox EIR builds upon the structure of the [COVID-19 vaccination delivery product](https://docs.dhis2.org/en/implement/health/covid-19-vaccine-delivery/covid-19-electronic-immunization-registry/design.html#cvc-eir-design), but with further simplifications to facilitate local customization and implementation. The Mpox EIR tracker retains the essential information and dependencies while offering greater flexibility for modifications. This guide provides the necessary instructions to customize and automate the tracker based on specific needs, ensuring that it is adaptable and easy to adjust for local requirements.
The current design of the Mpox EIR uses Mpox as a placeholder, but its simplified structure and flexibility make it easily adaptable for other vaccines, such as those for Ebola or other epidemic response efforts. This versatility allows for the expansion or reuse of the tracker in various vaccination efforts, ensuring it can support broader public health responses while maintaining core functionality.

![Stages and sections of the mpox immunisation registry](resources/image/eirmpox_001.png)

#### Enrollment Stage

The enrollment stage contains the core attribute to identify the patient - National and program UIDs, and identifiers. 

![Enrollment stage](resources/image/eirmpox_002.png)

#### Vaccination Stage

The vaccination stage is a repeatable stage that can be used for all the doses associated with a vaccine.

![Basic info and Risks](resources/image/eirmpox_003.png)

The **“Risk groups and underlying conditions”** section is used to flag whether the person belongs to a frontline group that puts them at a higher risk than the rest of the population. If “NO” the person is flagged as “Other” when it comes to PIs and also the aggregate dataset as shown above.
The program includes by default **HCWs, Animal handlers, and Veterinarians** - the latter being of particular importance for mpox due to the zoonotic pattern of the disease itself. Implementers can edit the options list and remove/edit/add options as relevant to the local context.

The gestational status appears only if the patient is a female.

The underlying conditions are added as possible counterindications for some vaccines. The default configuration includes **“Malignancy”, “Immunosuppression” and “Cardiovascular disease”**, but the DEs can be edited as needed. The Program currently does not include any alert associated with any of the conditions, but implementers can add those to either flag the possible counterindication or to block the data entry.

![Pre-immunisation questions](resources/image/eirmpox_004.png)

This is inherited from the C19 programme, where the previous infection was a deterrent for the administration of a dose. There is no PR associated with this DE and it is rather kept as a placeholder in case the tracker is used also for the immunisation efforts of other endemic-prone diseases that carry the same limitation pattern associated with previous infection. Implementers can easily remove this question if needed given teh lack of associated dependencies. 

![Vaccine administration](resources/image/eirmpox_005.png)

The vaccination information collects the key info of the vaccine, with its manufacturer, brand, batch number, and expiry date. The default configuration of this tracker takes into account just the mpox vaccine in its different nomenclatures, though it can be considered as a placeholder for the possibility of the addition of other vaccines for more epidemic-prone diseases. 

**The current configuration does not autoassign manufacturers** as it wishes to be as simple as possible. Should the auto assignation be required, the implementer could follow these steps:
Use the same code for the manufacturer and the brand if possible
- Create the PR “Assign Brand and manufacturers to [NAME OF VACCINE]" using the expression **`d2:hasValue( 'Vaccine_type' ) == true && #{Vaccine_type} == 'VACCINE'`**
- The action for this program rule is to assign value to the Data Element “Vaccine Manufacturer” as ‘VACCINE_CODE’ which is the option code for “VACCINE” as well as "VACCINE_CODE" for the brand.

The current configuration does not account for age limitations, but depending on the vaccine there can be lower age limits. If a vaccinator administers a dose to someone outside of that recommended age range, then a warning can be issued if needed.to do so:
- Create a PR → e.g. “If Age is under 18, then warn that VaccineX is recommended for ages 18 and up” with expression **`(#{Age_Calculated} < 18 ) && (#{Vaccine_type} =='VACCINEX')`**
- The action for these program rules is to show a warning: “This vaccine product is recommended for people 18 and older.”

The configuration assigns automatically the total number of doses required for the selected vaccine. The PR can be easily duplicated and assigned to other vaccines. Similarly, when the dose number equals the total number of required doses, the system also flags that the patient has received the final dose. 

The AEFI is associated with an alert soliciting the user to conduct an EFI investigation. SHould the AEFI occurr during the first dose, the answer is also automatically transposed in the next event, where the question in the Pre.Immunisation section “Has the patient had a severe allergic reaction after the first done?” is automatically populated with YES.

![AEFI alert in the second event](resources/image/eirmpox_006.png)

#### Scheduling the next dose

There is currently no way for a tracker to assign a date for the next event based on a data element, so what can be done is to configure the tracker to automatically autoschedule the next vaccination date to X days from the first dose. This must be modified to match the interval used in the country by changing the setting for the vaccination program stage in the maintenance app.

![Automatic generation of a n event after the time interval. 28 days was selected as it is the recommended interval for the mpox JYNNEOS vaccine](resources/image/eirmpox_007.png)

In addition, there can also be a data element that auto-assigns using program rules a recommended date depending on the vaccine product. 
- Create a PR “Assign a suggested date for next dose VACCINE X” with expression **`#{Vaccine_type} == 'VACCINEX' &&  d2:hasValue( 'Last_dose' ) == false && d2:hasValue( 'Dose_number' )== true`**
- The rule should act in two ways: 
  - firstly to show a warning next to the data element “suggested date for next dose” with the text “Next dose should be given at X days” - please note that the DE is automatically hidden when   the event is for the last dose of the vaccine
  - secondly assign a value to the data element “suggested date for next dose” with the expression **`d2:addDays( V{event_date}, XDAYS )`**

Scheduling an event is also possible in the Schedule tab next to the report tab:

![Schedule the next dose](resources/image/eirmpox_009.png)

This solution will also easily flag any overdue appointment for follow-up vaccinations. More information on this solution can be found in the [“Scheduled date in edit event form”](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/tracking-individual-level-data/capture.html#scheduled-date-in-edit-event-form) section of the Capture document. 

![Scheduling an event](resources/image/eirmpox_008.gif)

## Adverse Events Following Immunisation

The Mpox EIR tracker does not provide detailed analysis or reporting on Adverse Events Following Immunization (AEFIs) beyond the initial flagging of an immediate AEFI (severe and non-severe). For more comprehensive management of AEFIs, the Immunization Toolkit includes an [AEFI Tracker System Design](https://docs.dhis2.org/en/implement/health/immunization/adverse-events-following-immunization-aefi/design.html#imm-aefi-design) document, which outlines the configuration of a tracker program designed to support the notification, reporting, and investigation of AEFI cases at both national and sub-national levels. This document is intended for DHIS2 implementers and immunization program data managers to facilitate the localization and adaptation of the AEFI tracker to suit local workflows and national guidelines. The tracker data model in DHIS2 enables the tracking of individual AEFI cases over time, linking them with unique identifiers, and allows healthcare providers, program managers, and regulators to report, modify, and analyze AEFI data. This standalone program supports workflows from facilities to national-level investigations, functions as a repository for policy and regulatory decision-making, and includes standard indicators, dashboards, and notification features to enhance response times. 
It can be adopted independently or integrated with other DHIS2 tracker programs, such as the Immunization eRegistry.

## LMIS - Stock Management

Contrary to the design of the COVID-19 module, the LIMS component is not embedded within the aggregate vaccine delivery dataset for Mpox. This is because a standard [LMIS EPI metadata component](https://docs.dhis2.org/en/implement/health/immunization/epi-logistics/lmis-design.html) is already available and can be repurposed to track vaccine uptake or to better integrate Mpox data into existing LMIS tools.

However, if implementers wish to embed the LIMS component as it was done in the COVID-19 design, they can utilize the reference flat file provided in the [documentation](https://docs.dhis2.org/en/implement/health/covid-19-vaccine-delivery/covac-aggregate/overview.html) and the [metadata download](https://dhis2.org/metadata-downloads/) page. They can also consult the global generic LMIS toolkit linked to the EPI tools for additional guidance and integration.

## Dashboard and Analytics

Both the aggregate and tracker modules analyze the data through the EPI-Mpox dashboard.
Some visualizations (coverages) are linked to a Mpox Coverage legend with thresholds associated with colour codes to represent the percentage of teh coverage. Implementers can decide whether to keep it, adapt it, or remove it.

![Mpox dashboard](resources/image/epimpox_006.png)

### Indicators

The data exchange between the EIR and aggregate module was set up for all but the information on the staff availability.

The EIR in addition has three indicators that pull data only from the tracker module:
- MPOX-EIR - Drop-out rate JYNNEOS 30 days (%)
- MPOX-EIR - Vaccination records with complete contact information (%)
- MPOX-EIR - Vaccination records with complete batch/lot number information (%)

